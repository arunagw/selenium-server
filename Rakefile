require "rubygems"
require "selenium/client"
require 'selenium/rake/tasks'
Selenium::Rake::RemoteControlStartTask.new do |rc|
  rc.port = 4444
  rc.timeout_in_seconds = 3 * 60
  rc.background = true
  #rc.nohup = ENV['SELENIUM_RC_NOHUP'] == "true"
  rc.wait_until_up_and_running = true
  rc.additional_args << "-singleWindow"
end

Selenium::Rake::RemoteControlStopTask.new do |rc|
  rc.host = "localhost"
  rc.port = 4444
  rc.timeout_in_seconds = 3 * 60
  rc.wait_until_stopped = true
end

desc "Restart Selenium Remote Control"
task :'selenium:rc:restart' do
  Rake::Task[:"selenium:rc:stop"].execute [] rescue nil
  Rake::Task[:"selenium:rc:start"].execute []
end
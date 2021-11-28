# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative "config/application"

Rails.application.load_tasks

bin_path = ENV["BUNDLE_BIN"] || Rails.root.join("bin")

Rake::Task.define_task("pnpm:install") do
  Rake.sh("#{bin_path}/pnpm install")
end

if Rake::Task.task_defined?("assets:precompile") && File.exist?(Rails.root.join("bin", "yarn"))
  Rake::Task["assets:precompile"].enhance [ "pnpm:install" ]
end

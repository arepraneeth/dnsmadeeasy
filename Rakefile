require 'bundler/gem_tasks'
require 'rspec/core/rake_task'
require 'yard'

def shell(*args)
  puts "running: #{args.join(' ')}"
  system(args.join(' '))
end

task :permissions do
  shell('rm -rf pkg/ tmp/' )
  shell("chmod -v o+r,g+r * */* */*/* */*/*/* */*/*/*/* */*/*/*/*/*")
  shell("find . -type d -exec chmod o+x,g+x {} \\;")
end

task :build => :permissions

YARD::Rake::YardocTask.new(:doc) do |t|
  t.files = %w(lib/**/*.rb exe/*.rb - README.md LICENSE.txt)
  t.options.unshift('--title','DNS Client for DnsMadeEasy')
  t.after = ->() { exec('open doc/index.html') }
end

RSpec::Core::RakeTask.new(:spec)

task :default => :spec
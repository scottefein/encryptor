require 'rake'
require 'rake/testtask'
require 'rake/rdoctask' if RUBY_VERSION < '1.9.3'
require 'rdoc/task' if RUBY_VERSION >= '1.9.3'

desc 'Test the encryptor gem'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = true
end

desc 'Generate documentation for the encryptor gem'
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  rdoc.title    = 'Encryptor'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

if RUBY_VERSION < '1.9.3'
  require 'rcov/rcovtask'

  task :rcov do
    system "rcov -o coverage/rcov --exclude '^(?!lib)' " + FileList[ 'test/**/*_test.rb' ].join(' ')
  end

  desc 'Default: run unit tests under rcov.'
  task :default => :rcov
else
  desc 'Default: run unit tests.'
  task :default => :test
end

require 'bundler'
Bundler::GemHelper.install_tasks

require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec)
task :default => :spec

namespace :spec do

  desc "Run all specs on multiple ruby versions (requires rvm and bundler)"
  task :portability do
    %w[1.8.7 1.9.2 ree rbx jruby].each do |version|
      system <<-BASH
        bash -c 'source ~/.rvm/scripts/rvm;
                 rvm #{version};
                 echo "--------- version #{version} ----------\n";
                 bundle install 1> /dev/null;
                 rake spec'
      BASH
    end
  end

end
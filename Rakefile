require 'junoser'

config_path = './config/**/*.txt'

desc 'Run tests'
task :test do
  Dir[config_path].inject(true) {|passed, path|
    print "verifying #{path} ... "
    if open(path) {|f| Junoser::Cli.commit_check(f) }
      puts "done"
      passed
    else
      puts "failed"
      false
    end
  } || abort
end

task default: :test

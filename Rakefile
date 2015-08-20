require 'junoser'

config_path = './config/**/*.conf'

def is_juniper?(str)
  str =~ /^version \S+;$/m
end

desc 'Run tests'
task :test do
  Dir[config_path].inject(true) {|passed, path|
    config = File.read(path)

    unless is_juniper?(config)
      puts "skip #{path}"
      next passed
    end

    print "verifying #{path} ... "

    if Junoser::Cli.commit_check(config)
      puts 'done'
      passed
    else
      puts 'failed'
      false
    end
  } || abort
end

task default: :test

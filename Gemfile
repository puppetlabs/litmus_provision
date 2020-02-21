source ENV['GEM_SOURCE'] || 'https://rubygems.org'

source "https://1y1Ff1-LqCPQdPUv5kKSLLjbsewUFfkgVs@gem.fury.io/davids/"
gem 'bolt'
gem 'puppet_litmus'
ruby_version_segments = Gem::Version.new(RUBY_VERSION.dup).segments
minor_version = ruby_version_segments[0..1].join('.')
group :development do
  gem "puppet-module-posix-default-r#{minor_version}", require: false, platforms: [:ruby]
  gem "puppet-module-posix-dev-r#{minor_version}",     require: false, platforms: [:ruby] , :source => "https://1y1Ff1-LqCPQdPUv5kKSLLjbsewUFfkgVs@gem.fury.io/davids/"
  gem "puppet-module-win-default-r#{minor_version}",   require: false, platforms: %i[mswin mingw x64_mingw]
  gem "puppet-module-win-dev-r#{minor_version}",       require: false, platforms: %i[mswin mingw x64_mingw]
  gem 'github_changelog_generator',                    require: false, git: 'https://github.com/skywinder/github-changelog-generator', ref: '20ee04ba1234e9e83eb2ffb5056e23d641c7a018' if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.2.2')
end

# Evaluate Gemfile.local and ~/.gemfile if they exist
extra_gemfiles = [
  "#{__FILE__}.local",
  File.join(Dir.home, '.gemfile'),
]

extra_gemfiles.each do |gemfile|
  if File.file?(gemfile) && File.readable?(gemfile)
    eval(File.read(gemfile), binding)
  end
end
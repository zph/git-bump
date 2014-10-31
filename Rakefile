require "bundler/gem_tasks"

desc "standalone scripts"
task :standalone do
  lib_lines = File.read("lib/git_bump.rb").split("\n")
  bin_lines = File.read("bin/git-bump").split("\n")

  bad_lines = [
    "$:.unshift(File.expand_path('../../lib', __FILE__))",
    "require 'git_bump'",
    "#!/usr/bin/env ruby",
  ]

  bin_lines -= bad_lines
  all_lines = ["#!/usr/bin/env ruby",*lib_lines, *bin_lines]
  File.write("standalone/git-bump", all_lines.join("\n"))
  `chmod +x standalone/git-bump`
end

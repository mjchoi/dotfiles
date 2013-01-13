namespace :dots do
  namespace :git do
    desc "clean up the git repo in ~"
    task :clean do
      `mv .git .git_disabled`
    end

    desc "bring back the git repo in ~ (useful for publishing changes)"
    task :restore do
      `mv .git_disabled .git`
    end
  end

  namespace :janus do
    desc "link vim config files"
    task :symlink do
      if File.exists?('.vimrc') || File.exists?('.gvimrc')
        abort ".vimrc or .gvimrc already exists (don't link twice)"
      end

      Dir.chdir('.vim') do
        `rake link_vim_conf_files`
      end
    end
  end
end

desc "install dotfiles & clean up"
task :default do
  Rake::Task["dots:janus:symlink"].invoke
  Rake::Task["dots:git:clean"].invoke
end

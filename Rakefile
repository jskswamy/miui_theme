require 'fileutils'

desc 'Create mtz file'
task :build do
  theme_name = "Dark"
  temp_dir = "tmp/"
  theme_files = []
  excluded_dirs = ["preview", "wallpaper"]

  FileUtils.remove_dir(temp_dir) if Dir.exists?(temp_dir)
  FileUtils.mkdir (temp_dir)
  FileUtils.cp_r theme_name, temp_dir
  Dir.chdir("#{temp_dir}/#{theme_name}")
  theme_files = Dir.glob("*") - excluded_dirs

  theme_files.each do |dir_name|
    if Dir.exist?(dir_name)
      system "zip -r #{dir_name}.zip #{dir_name}"
      FileUtils.rm_r(dir_name)
      FileUtils.mv("#{dir_name}.zip", dir_name)
    end
  end

  Dir.chdir("../")
  system "zip -r #{theme_name}.mtz #{theme_name}"
  FileUtils.rm_r(theme_name)
end

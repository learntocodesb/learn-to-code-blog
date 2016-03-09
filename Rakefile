desc "build _site"
namespace :assets do
  task :precompile do
    puts `bundle exec jekyll build`
  end
end

desc "generate post"
namespace :posts do
  task :generate do
    post_date = Time.now
    file_date = post_date.strftime("%F")
    file_title = ENV['title']

    if file_title.nil?
      $stderr.puts "Usage: rake posts:generate title=title-of-post"
      exit 1
    end

    post_title = file_title.split("-").map(&:capitalize).join(" ")
    post_filename = [file_date, file_title].join("-") + ".markdown"
    post_filepath = File.join("_posts", post_filename)

    if File.exists?(post_filepath)
      $stderr.puts "#{post_filepath} already exists"
      exit 1
    end

    post = open(post_filepath, "w")
    post.write [
      "---",
      "layout: post",
      "title: #{post_title}",
      "author: Fred Savage",
      "author_github: fredsavage",
      "date: #{post_date}",
      "categories: ",
      "---"
    ].join("\n")
  end
end

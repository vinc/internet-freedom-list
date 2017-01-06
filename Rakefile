require "rake"
require "redcarpet"

desc "build index.html"
task :default do
  markdown = Redcarpet::Markdown.new(Redcarpet::Render::HTML)
  puts "Generating index.html"
  File.open("README.md", "r") do |input|
    html = markdown.render(input.read)
    File.open("index.html", "w") do |output|
      output.write(template { html })
    end
  end
end

def template(&block)
  <<-HTML.gsub(/^\s+/, "")
    <!doctype html>
    <html>
      <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Internet Freedom List</title>
      </head>
      <body>
        #{yield}
      </body>
    </html>
  HTML
end

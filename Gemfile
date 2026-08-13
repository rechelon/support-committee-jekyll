source "https://rubygems.org"

# This pins the theme to whatever Jekyll/plugin versions GitHub Pages
# itself runs, so a site that builds locally will also build correctly
# when GitHub builds it for you. If you're hosting elsewhere and want
# newer Jekyll features, swap this gem for a normal `gem "jekyll"` line.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-feed"
end

# Windows/JRuby support some GitHub Pages users still need
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", platforms: [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", platforms: [:jruby]

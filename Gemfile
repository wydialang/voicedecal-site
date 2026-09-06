source "https://rubygems.org"

# Jekyll + the Just the Docs theme.
# You do NOT need to install these locally to maintain the site — GitHub Actions
# builds and deploys the site on every push (see .github/workflows/pages.yml).
# This Gemfile only matters if you want to preview the site on your own machine.
gem "jekyll", "~> 4.4"
gem "just-the-docs", "~> 0.10"

group :jekyll_plugins do
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Windows and JRuby do not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows.
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

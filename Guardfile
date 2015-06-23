#-*- mode: ruby; coding: utf-8 -*-

pwd=File.expand_path(File.dirname(__FILE__))
guard 'shell' do
  watch(/^.+\.adoc$/)  do |m|
    system("rake html")
  end
end


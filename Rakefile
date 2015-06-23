# -*- mode: ruby; coding: utf-8 -*-
desc "Ascii Docをコンパイルする(defaultはhtml)"
task :default => :html

require 'asciidoctor'
require 'asciidoctor/cli'
require 'asciidoctor-diagram'

doc = "adoc-template.adoc"
basename = File.basename doc, ".*"
desc "htmlへ変換"
task :html do
  invoker = Asciidoctor::Cli::Invoker.new [doc]
  invoker.invoke!
  invoker.code
end

desc "pdfへ変換"
task :pdf do
  require 'asciidoctor-pdf'
  opts = %w(-b pdf -a pdf-style=my-theme.yml --trace)
  invoker = Asciidoctor::Cli::Invoker.new [doc, opts].flatten
  invoker.invoke!
  invoker.code
end

desc "pdfへ変換"
task :tex do
  font_main = "ヒラギノ明朝 Pro"
  font_sans = "ヒラギノ角ゴ Pro"
  font_mono = "Ricty"
  system( "export LANG=ja_JP.UTF-8; a2x --no-xmllint -a lang=ja -d article -f pdf --dblatex-opts='-b xetex -P doc.publisher.show=0 -P latex.output.revhistory=0 -P xetex.font=\"\\setmainfont{#{font_main}}&#10;\\setsansfont{#{font_sans}}&#10;\\setmonofont{#{font_mono}}&#10;\\XeTeXlinebreaklocale \"ja\"&#10;\"' #{doc}")
end



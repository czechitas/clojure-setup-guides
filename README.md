# Instalační návody pro Clojure workshop

Tyto návody se snaží o nejpřímější a snad i uživatelsky nejvíce pochopitelnou cestu, jak instalovat [Javu](https://java.com), [Leiningen](https://leiningen.org) a [Gorilla REPL](http://gorilla-repl.org). Tento software potřebují mít na svém počítači účastnice Clojure workshopu pořádaného [Czechitas](https://www.czechitas.cz) a skupinou [Prague Lambda Meetup](https://www.meetup.com/Lambda-Meetup-Group/).

Návody jsou dostupné pro následující operační systémy:

- [Windows 10](windows.md)
- [macOS 10.12 „Sierra“](macos.md)
- [Ubuntu 16.10 „Yakkety Yak“](ubuntu.md)
- [Fedora 24](fedora.md)


## Závislosti

- [Ruby](https://www.ruby-lang.org) 2.3.1
- [Bundler](http://bundler.io) ≥ 1.12.5


## Instalace

```bash
bundle install
```

## Opravy, rozvoj a distribuce

Projekt je určený k prezentaci přes [GitHub Pages](https://pages.github.com) s použitím [Jekyllu](http://jekyllrb.com) a standrdního [GitHub Pages pluginu](https://github.com/github/pages-gem) s [tématem vzhledu minima](https://github.com/jekyll/minima).

Před úpravami je vhodné aktualizovat závislosti kvůli možným změnám v GitHub Pages pluginu:

```bash
bundle update
```

Než pusheme změny na GitHub a tím je rovnou nasadíme je dobré zkontrolovat, zda stránka funguje, což lze provést i lokálně:

```bash
bundle exec jekyll serve
```


## Licence

Všechny návody jsou volné dílo.

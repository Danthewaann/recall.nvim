# Changelog

All notable changes to Recall will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0](https://github.com/fnune/recall.nvim/releases/tag/1.2.0) - 2025-05-28

### Added

- Added support for the [`snacks.nvim`](https://github.com/folke/snacks.nvim) picker (thanks to @shihanng's [PR](https://github.com/fnune/recall.nvim/pull/9))

## [1.1.2](https://github.com/fnune/recall.nvim/releases/tag/1.1.2) - 2024-03-11

### Fixed

- Fixed a bug whereby Recall would clear all signs with its `BufEnter` autocommand, due to a misuse of the `sign_*` APIs
  (https://github.com/fnune/recall.nvim/issues/7)

## [1.1.1](https://github.com/fnune/recall.nvim/releases/tag/1.1.1) - 2024-03-11

### Fixed

- Fixed 'No write since last change' when trying to open a mark while the current buffer has unsaved changes
  (https://github.com/fnune/recall.nvim/issues/4)
- Fixed bug in Telescope integration where hitting enter in insert mode would actually remove a mark instead of
  navigating to it (https://github.com/fnune/recall.nvim/issues/6)
  - This was happening because the default mapping was `<C-m>`, and as far as Vim/Neovim are concerned, `<C-m>` and
    `<CR>` [are the same thing](https://groups.google.com/g/vim_dev/c/2bp9UdfZ63M/m/sajb9KM0pNYJ?pli=1)

### Changed

- The default mapping to delete marks from the Telescope extension is now `<M-d>`; see **Fixed**

## [1.1.0](https://github.com/fnune/recall.nvim/releases/tag/1.1.0) - 2024-03-09

### Added

- Show mappings legend within Telescope picker

### Changed

- Fix recommendation on how to unset mappings for Telescope: previous
  recommendation `nil` did not work with `tbl_{deep_}extend`, an empty string
  will do

### Fixed

- Use `tbl_deep_extend` instead of `tbl_extend` to correctly merge user options
  with defaults

## [1.0.0](https://github.com/fnune/recall.nvim/releases/tag/1.0.0) - 2024-03-08

### Added

Initial release of Recall.

- Basic global mark management with `:Recall{Toggle,Mark,Unmark}` and
  `:RecallClear`
- Basic global mark navigation with `:Recall{Next,Previous}`
- Sign column with a customizable character
- Support for Neovim 0.10.x and also 0.9.x and lower
- Telescope integration beyond the built-in `:Telescope marks` that allows mark
  deletion and displaying only global marks
- Improved stability by adding CI and testing using [plenary][plenary-tests]

[plenary-tests]: https://github.com/nvim-lua/plenary.nvim/blob/master/TESTS_README.md

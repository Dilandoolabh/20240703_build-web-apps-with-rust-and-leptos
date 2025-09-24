# Changelog

## [Unreleased]

## [0.3.0] - Apr 16 2023

### Changes

- both the `line_of_byte()` and `byte_of_line()` methods on `Rope`s and
  `RopeSlice`s now interpret their argument as byte and line offsets,
  respectively. This allows those methods to accept the full byte length or
  line length of the `Rope`/`RopeSlice` as a valid argument without panicking;

### Bug fixes

- fixed a very rare bug where the `Lines` iterator would include the trailing
  `'\r'` if a line was terminated by a CRLF which was split across consecutive
  chunks;

### Performance

- the `byte_slice()` method on `Rope`s and `RopeSlice`s is around 10% faster;


## [0.2.0] - Mar 26 2023

### Performance

- the leaves of the B-tree are now gap buffers instead of simple `String`s,
  which improves the performance of consecutive edits applied to the same
  cursor position. This alone resulted in a 8-15% improvement in the
  [crdt-benchmarks](https://github.com/josephg/crdt-benchmarks), and together
  with other tweaks it makes `v0.2` 80-90% faster than `v0.1` on those editing
  traces;

- `RopeBuilder::append()` is around 20% faster;

### Breaking changes

- the `Chunks` iterator no longer implements `ExactSizeIterator`;

[Unreleased]: https://github.com/noib3/crop/compare/v0.3.0...HEAD
[0.3.0]: https://github.com/noib3/crop/compare/v0.2.0...v0.3.0
[0.2.0]: https://github.com/noib3/crop/compare/v0.1.0...v0.2.0

# CRAN comments

## Resubmission of an archived package

sglOptim was archived on CRAN on 2024-01-12
("Archived on 2024-01-12 as issues were not corrected despite reminders.").
The package has a new maintainer (Zhiwei Xiao) as of this release, with the
previous maintainer's (Niels Richard Hansen) knowledge and approval.

The issues recorded in the pre-archival check results
(https://cran-archive.r-project.org/web/checks/2024/2024-01-12_check_results_sglOptim.html)
have been addressed:

* WARNING (format string is not a string literal, `inst/include/rtools.h`):
  fixed by passing the message through a `"%s"` format literal instead of
  passing it directly as the format string.
* NOTE (lost braces in `\itemize`, `sgl_predict.Rd` / `sgl_subsampling.Rd`):
  fixed by using `\describe{}` for the named list items that were previously
  (incorrectly) nested inside `\itemize{}`.
* NOTE (installed size ~11.7Mb on macOS): this is inherent to the compiled
  Armadillo/Rcpp-based template library and has not changed.

Additional maintenance done in this release:

* Modernized `inst/CITATION` (`bibentry()`/`c(person(...))` instead of the
  deprecated `citEntry()`/`personList()`).
* Fixed a stale HTTP link and removed a publisher URL that CRAN's URL check
  flagged as blocked (403).
* Removed a `\doi`-style URL from `DESCRIPTION`'s `URL` field (the DOI is
  already correctly recorded via `inst/CITATION`'s `doi` field).
* Modernized package-level documentation from `@docType package` to
  `"_PACKAGE"` and added `Encoding: UTF-8` to `DESCRIPTION`.

## R CMD check results

`devtools::check()` / `R CMD check --as-cran` locally (macOS, R 4.5.3):
0 errors | 0 warnings | 2 notes

* `checking CRAN incoming feasibility ... NOTE`: "New submission" /
  "Package was archived on CRAN" — expected, since this is a resubmission
  of a previously archived package.
* `checking HTML version of manual ... NOTE`: HTML validation was skipped
  locally because this machine's `tidy` binary is outdated. This is a
  local tooling limitation, not a package issue.

GitHub Actions CI (r-lib/actions `check-standard`) additionally checks the
package on windows-latest and ubuntu-latest.

## Downstream dependencies

There are currently no reverse dependencies on CRAN. `msgl`, a former
dependent package, was cascade-archived on the same date
("requires archived package 'sglOptim'") and is not currently on CRAN.
`lsgl` was archived earlier (2018) for an unrelated reason.

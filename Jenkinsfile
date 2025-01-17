name: 'Run PMD static code analyzer'
description: 'Analyse code with PMD'
author: 'Amit Kumar'

inputs:
  rulesets:
    description: Comma-separated list of ruleset or rule references.
    required: true
  dir:
    description: Directory for the analyzed sources (relative to the repo root)
    required: true
    default: '.'
  format:
    description: Output format of the analysis report (see https://pmd.github.io/latest/pmd_userdocs_report_formats.html).
    required: false
  encoding:
    description: Specifies the character set encoding of the source code files PMD is reading. The valid values are the standard character sets of java.nio.charset.Charset.
    required: false
  failOnViolation:
    description: |
      Specifies whether PMD exits with non-zero status if violations are found.
      By default PMD exits with status 4 if violations are found.
      Disable this feature withfailOnViolation false to exit with 0
      instead and just output the report.
    required: true
    default: 'true'
  language:
    description: Specify the language PMD should use
    required: false
    default: 'java'
  minimumpriority:
    description: Rule priority threshold; rules with lower priority than configured here won't be used.
    required: false
  showsuppressed:
    description:  	Causes the suppressed rule violations to be added to the report.
    required: false
  version:
    description: Specify the version of a language PMD should use. Used together with language
    required: false
  reportfile:
    description: Path to a file to which report output is written. The file is created if it does not exist. If this option is not specified, the report is rendered to standard output.
    required: false
  shortnames:
    description: Prints shortened filenames in the report
    required: false
  cache:
    description: Specify the location of the cache file for incremental analysis. This should be the full path to the file, including the desired file name (not just the parent directory).
    required: false
  auxclasspath:
    description: |
      Specifies the classpath for libraries used by the source code. This is used to resolve types
      in source files. The platform specific path delimiter (":" on Linux, ";" on Windows) is used
      to separate the entries. Alternatively, a single file: URL to a text file containing path
      elements on consecutive lines can be specified.
    required: false
  verbose:
    description: Debug mode. Prints more log output.
    required: false
  filelist:
    description: Path to file containing a comma delimited list of files to analyze. If this is given, then you don't need to provide -dir.
    required: false
  force-language:
    description: Force a language to be used for all input files, irrespective of filenames.
    required: false
  norulesetcompatibility:
    description: Disable automatic fixing of invalid rule references.
    required: false
  no-cache:
    description: Explicitly disables incremental analysis.
    required: false
  suppressmarker:
    description: Specifies the comment token that marks lines which PMD should ignore.
    required: false
  threads:
    description: Sets the number of threads used by PMD. Set threads to 0 to disable multi-threading processing.
    required: false

runs:
  using: 'docker'
  image: 'docker://rawdee/pmd:6.40.0_2'
  args:
    - -rulesets
    - ${{ inputs.rulesets }}
    - ${{ (inputs.filelist && '-filelist') || '-dir' }}
    - ${{ inputs.filelist || inputs.dir }}
    - ${{ inputs.format && '-format' }}
    - ${{ inputs.format }}
    - ${{ inputs.encoding && '-encoding' }}
    - ${{ inputs.encoding }}
    - -failOnViolation
    - ${{ inputs.failOnViolation }}
    - ${{ inputs.language && '-language' }}
    - ${{ inputs.language }}
    - ${{ inputs.version && '-version'}}
    - ${{ inputs.version }}
    - ${{ inputs.minimumpriority && '-minimumpriority' }}
    - ${{ inputs.minimumpriority }}
    - ${{ inputs.reportfile && '-reportfile' }}
    - ${{ inputs.reportfile }}
    - ${{ inputs.cache && '-cache' }}
    - ${{ inputs.cache }}
    - ${{ inputs.showsuppressed && '-showsuppressed'}}
    - ${{ inputs.shortnames && '-shortnames'}}
    - ${{ inputs.auxclasspath && '-auxclasspath'}}
    - ${{ inputs.auxclasspath }}
    - ${{ inputs.verbose && '-verbose'}}
    - ${{ inputs.force-language && '-force-language'}}
    - ${{ inputs.force-language }}
    - ${{ inputs.norulesetcompatibility && '-norulesetcompatibility'}}
    - ${{ inputs.no-cache && '-no-cache'}}
    - ${{ inputs.suppressmarker && '-suppressmarker' }}
    - ${{ inputs.suppressmarker }}
    - ${{ inputs.threads && '-threads' }}
    - ${{ inputs.threads }}

branding:
  icon: 'flag'
  color: 'red'

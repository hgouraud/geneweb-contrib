# GeneWeb-contrib: lex-utils

Tool for lexicon management

## Usage

cat script.ml | [ GWREPL_VERBOSE=1 ] [ GWREPL_FORCE_UNPACK=1 ]
   [ GWREPL_NOPROMPT=1 ] gwrepl.exe [script_arg1] ...

## Options
  ; ("-check", Arg.String (fun s -> check := true; lexicon_2 := s)
    Compares lexicon_2 entries against main lexicon. Reports new entries appearing
    in lexicon_2.
    If -merge is set, merges lexicon_2 "non new" entries into main lexicon.
    
  ; ("-extract", Arg.String (fun s -> extract := true ; lang_2 := String.split_on_char ',' s)
    Extracts entries on main lexicon for a set of languages. typical use is fr,xx
    Language fr being the most completely defined language, this action will report
    existing and missing translations for language xx.

  ; ("-missing", Arg.Set missing
    Scans the whole repo for missing translations for all languages. Too bulgy
    
  ; ("-missing-lang", Arg.String (fun s -> missing := true ; lang := String.split_on_char ',' s)
    Same as -missing, but use a comma-separated list of lang instead of the default one.
    Use if -extract fr,en, xx,yy produces the same result for languages xx and yy.

  ; ("-only", Arg.Set only
    If -only is not set, lex_util will read all *.txt files in any repo sub-folder named lex.
    Thsi includes among possible others the plugin area.
    If -only is set, lex_util will process only the lexicon designated in the command line.

  ; ("-orphans", Arg.Set orphans
    Check missing or unused keyword. -repo must be defined.")
  ; ("-log", Arg.Set log
    Option for orphans. Print in log files instead of stdout.

  ; ("-repo", Arg.String (fun x -> repo := x)
    Define repo location. If repo is defined, lexicon is relative to repo.

  ; ("-sort", Arg.Set lex_sort
    Sort the lexicon (both key and content).
    Options -merge and -first define the behaviour in case of multiple entries.
    For a typical usage, concatenate lexicon_1.txt and lexicon_2.txt and apply sort
    -merge will add new language entries appearing in lexicon_2
    -first will keep language entries  of lexicon_1 if they appear also in lexicon_2
  ; ("-first", Arg.Set first
    If multiple language entries, select first occurence.
  ; ("-merge", Arg.Set merge
    Merge rather than replace new lexicon entries (both key and content).
  
  

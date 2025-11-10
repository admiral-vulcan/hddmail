# Repository guidelines

- Scope: Applies to the entire repository.
- Keep user-facing output, email content, and inline comments in English when
  introducing new code.
- Use the `BASE_DIR`, `CFG_PATH`, `STATUS_STORE_PATH`, and `EXEC_PATH`
  constants that are declared in `hddexec` instead of hard-coded paths.
- Prefer POSIX-compatible shell syntax in `hddexec`; avoid Bash-only features
  unless the script explicitly requires Bash.
- Update `README.md` whenever command-line options or installation steps change.

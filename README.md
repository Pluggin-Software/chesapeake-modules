# Chesapeake modules

The catalog the Chesapeake Framework's **Add Module** store reads: `index.json`.

To list a module, open a pull request adding it to `index.json`:

- `repository` is the module's own GitHub repository (`owner/repo`), holding the module's folder contents and a `module.json`.
- Each version names a git **tag** (never a branch) and the SHA-256 of that tag's zip, as GitHub serves it:

  ```bash
  curl -sL https://api.github.com/repos/OWNER/REPO/zipball/refs/tags/TAG | shasum -a 256
  ```

- `version`, `core` and `requires` match the tag's `module.json`, and `version` matches its `config.php` `version_number`.

A published tag is never moved: the hash would stop matching and installs would be refused.

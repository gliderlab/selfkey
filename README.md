# Selfkey

> Executable-to-Database Binding Tool (Go)

Selfkey binds a SQLite database to your executable using an embedded instance key.

## Usage

```bash
go build -o selfkey main.go
./selfkey
```

Output:
```
OK: /path/to/selfkey bound to /path/to/selfkey.db
```

## How It Works

1. **First run**: Generates a unique key and embeds it in the executable
2. **Creates DB**: `yourapp.db` next to `yourapp` executable
3. **Each run**: Validates executable matches bound database

## CLI Flags

| Flag | Description |
|------|-------------|
| `--rebind` | Allow rebinding to current executable (for migrations) |

## Database

- **Path**: `{executable_name}.db`
- **Log**: `{executable_name}.log`

**Tables:**
- `meta` - key/value metadata (instance_key, exe_path, bound_at, etc.)
- `starts` - execution history

## Security

- 32-byte hex instance key embedded in executable
- Prevents database/executable mismatch
- Use `--rebind` to migrate to new executable path

## License

MIT

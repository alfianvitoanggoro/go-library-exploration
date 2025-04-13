# go-library-exploration
Documentation of all library golang for knowledge

## 📦 GO WORK

### Workspace Management with <code> go work </code>
This project uses Go Workspaces (go work) to manage multiple modules (one per library) within a single repository. This makes it easy to:

- Run and develop each module independently

- Avoid manual replace directives

- Share code between modules if needed

- Maintain clean, isolated dependencies per module

<b>*Requires Go 1.18+</b>

### Initialize go.work
At the root of your project:

```bash
go work init ./redis ./kafka ./cobra
```
This will generate a go.work file like this:
<pre>
go 1.24

use (
	./redis
	./kafka
	./cobra
)
</pre>

### Add a New Module to the Workspace
If you add a new folder (e.g., grpc/), run:
```bash
go work use ./grpc
```

### Remove a Module from the Workspace
You can either manually remove the folder from the go.work file, or run:
```bash
go work edit -dropreplace ./kafka
```
Note: This only removes it from the workspace, not from the filesystem.

### Running Code in a Module
Each module is self-contained with its own go.mod. You can cd into any module and run it:
```bash
cd redis
go run main.go
```

Or run tests:
```bash
go test ./...
```

### Tips
- Use go work to keep multi-library explorations organized

- You can commit the go.work file for team use (optional)

- Each folder is a standalone module with its own go.mod


## 📝 Structure
<pre>
go-library-exploration/
│
├── README.md               ← Dokumentasi utama repo (daftar library, tujuan, dll)
├── go.work                 ← (opsional) Workspace untuk mengelola banyak module
│
└── [name of library]/      ← Eksplorasi untuk library Cobra
    ├── go.mod              ← Modul Go lokal untuk Cobra
    ├── main.go             ← Contoh implementasi utama
    ├── README.md           ← Penjelasan & catatan khusus Cobra
    ├── internal/           ← (opsional) Struktur package jika ingin modular
    ├── config.yaml         ← (opsional) Contoh file config
    ├── docker-compose.yml  ← (opsional)
    ├── dockerfile          ← (opsional)
    └── .env                ← (opsional) konfigurasi koneksi db
</pre>



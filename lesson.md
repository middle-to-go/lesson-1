



[TOC]













---















📽️ - посмотри воркшоу

⚗️ - проведи эксперимент

🔬 - изучи внимательно

📖 - прочитай документация

🪙 - подумай о сложности

🐞 - запомни ошибку

🏔️ - обойди камень предкновенья

⏰ - сделай перерыв

🏡 - попробуй дома

💡 - обсуди светлые идеи

















---



















## Язык Go



























---

### История













**Go** was designed at Google in **2007** to improve <u>programming productivity</u> in an era of multicore, networked machines and large codebases.



Go was publicly announced in November **2009**, and version **1.0** was released in March **2012**. Go is widely used in production at Google and in many other organizations and <u>open-source</u> projects.



**Robert "Rob" C. Pike** (born **1956**) is a Canadian 🇨🇦 programmer and author. He is best known for his work on the Go programming language and at <u>Bell Labs</u>, where he was a member of the <u>Unix</u> team.



**Kenneth Lane Thompson**  (born **1943**) is an American 🇺🇸 pioneer of computer science. Thompson worked at <u>Bell Labs</u> for most of his career where he designed and implemented the original <u>Unix</u> operating system. Since **2006**, Thompson has worked at Google, where he co-invented the Go programming language.











---

### Характеристики

**Парадигмы**

- компилируемый
- императивный
- структурированный
- многопоточный

**Возможности**

- Cтрогая статическая типизация
- Утиная типизация
- Строковый тип со встроенной поддержкой юникода
- Автоматическое управление памятью со сборщиком мусора
- Интеграция с кодовой базой, написанной на языке **C**

**Ограничения**

- По крайней мере сейчас Go не подходит для разработки **UI**
- По крайней мере сейчас Go не подходит для обобщенного программирования
- По крайней мере сейчас Go не имеет механизма переопределения методов

**Имплементации**

- gc
- gccgo

**Вдохновлен**

| Odin lang | Crystal lang | C lang | Unix |
| :-------: | :----------: | :----: | :--: |

---

### Версии

...

- [ ] **1.11** 2018-08
  - добавлен новый механизм версионирования пакетов и управления зависимостями - <u>модули</u>

- [ ] **1.12** 2019-02

- [ ] **1.13** 2019-09
  - добавлены в язык новые числовые литералы
  - разрешена операция побитового сдвига для целых чисел со знаком

- [ ] **1.14** 2020-02
  - разрешено включать несколько интерфейсов, имеющих одноимённые методы с идентичными сигнатурами

- [ ] **1.15** 2020-08 

- [ ] **1.16** 2021-02
  - по умолчанию включен режим с поддержкой модулей

- [ ] **1.17** 2021-08
  - конвертация слайсов в указатель массива

- [ ] **2.00** xxxx-xx <u>generic</u>-и 🏆



> Each major Go release is supported until there are two newer major releases. For example, Go 1.5 was supported until the Go 1.7 release, and Go 1.6 was supported until the Go 1.8 release.

> If all goes well it will be available in the Go 1.18 release.

---





















## Рабочее окружение

























---

### Инсталяция

Для установки достаточно воспользоваться пакетным менеджером

```sh
# Homebrew
➜ brew install go # or upgrade
➜ go version
go version go1.16.3 darwin/amd64
```

```sh
# Ubuntu
➜ sudo apt install golang
➜ go version
go version go1.13.8 linux/amd64
```

```sh
➜ brew info go
go: stable 1.16.3 (bottled), HEAD
# ...

➜ brew info --json go | jq -r '.[].versioned_formulae[]'
go@1.15
# ...
go@1.9

➜ brew install go@1.11
```

```shell
➜ go get golang.org/dl/go1.15
➜ go1.15 download
➜ go1.15 env GOROOT
/Users/creator/sdk/go1.15
```

```sh
➜ echo "export GOPATH=~/go" >> ~/.{profile} # zshrc, bashrc, ...
```

---

### Расположения

```shell
➜ brew list go
# bin/, links, etc 📽️

➜ go env GOROOT
/usr/local/Cellar/go/1.16.3/libexecls
```

```sh
➜ tree -L 2 $GOPATH
/Users/creator/go
├── bin
│   └── gopls
├── pkg
│   ├── darwin_amd64
│   ├── linux_amd64
│   ├── mod
│   └── sumdb
└── src # Git, Mercurial, Bazaar
    ├── github.com
    ├── golang.org
    ├── google.golang.org
    └── gopkg.in
    
➜ export PATH=$PATH:$GOPATH/bin # стоит добавить в shell profile
```

```shell
➜ tree -L 1 pkg/errors
pkg/errors
├── ...
├── errors.go
└── errors_test.go

➜ ls $GOPATH/pkg/darwin_amd64/github.com/pkg/errors/
# errors.a
```

---

### Переменные

```sh
➜ go env GOENV
# /Users/creator/Library/Application Support/go/env
```

```sh
➜ go env
GO111MODULE=""
GOARCH="amd64"
GOBIN=""
GOCACHE="/Users/creator/Library/Caches/go-build"
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="darwin"
GOINSECURE=""
GOMODCACHE="/Users/creator/go/pkg/mod"
GONOPROXY=""
GONOSUMDB="*.ozon.ru"
GOOS="darwin"
GOPATH="/Users/creator/go"
GOPRIVATE=""
GOPROXY="direct"
GOROOT="/usr/local/Cellar/go/1.16.3/libexec"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/usr/local/Cellar/go/1.16.3/libexec/pkg/tool/darwin_amd64"
GOVCS=""
GOVERSION="go1.16.3"
GCCGO="gccgo"
AR="ar"
CC="clang"
CXX="clang++"
CGO_ENABLED="1"
GOMOD="/Users/creator/go/src/github.com/ozoncp/ocp-task-api/go.mod"
...
```



---





















## Программа



























---

### Точка входа



```go
package main

import "fmt"

func main() {
	fmt.Println("hello world 👋")
}
```

```go
package main

import (
	"fmt"
  "github.com/enescakir/emoji"
)

func main() {
  fmt.Printf("hello world %v", emoji.WavingHand.Tone(emoji.Dark))
}
```

```sh
➜ cd `mktemp -d`
➜ pbpaste > hello-world.go
```

```sh
➜ go build -o hello-world ./hello-world.go
➜ ./hello-world.go
# hello world 👋🏿
```

- [ ] Форматированный вывод 🏡

---

### Пакет

> A package is a collection of source files in the same directory that are compiled <u>together</u>. Functions, types, variables, and constants defined in one source file are visible to all other source files within the same package.

Описание:

- ключевое слово: `package`
- наименование: `under_score`
- расположение: `$GOPATH`
- экспортируемые функции: `CamelNotation` + `CapitalLetter`
- инициализация: `func init()`
- импортирование: 
  - одиночное
  - множественное `()`
  - с псевдонимом `alias`
  - новые версии `v2`
  - без квалификации при использование `.`
  - для инициализации `_`

```go
import (
  "fmt"
	emoji "github.com/enescakir/emoji"
  emoji "github.com/kyokomi/emoji/v2" // ❌ conflict
  _ "github.com/lib/pq"
)
```

- [ ] Порядок импортирования  и механизм **custom import paths** 🏡

---

### Модуль

> A repository contains one or more modules. A module is a collection of related Go packages that are released together. A Go repository typically contains only one module, located at the root of the repository.

```sh
➜ go mod init [github.com/{group}/{repo}] 
# github.com/creator/hello-world
```

```go
module github.com/creator/hello-world
go 1.16 // минимальная версия Go
```

```
➜ go get github.com/enescakir/emoji
```

```go
module github.com/creator/hello-world
go 1.16
require github.com/enescakir/emoji v1.0.0 // indirect
```

```sh
➜ go mod tidy
```

```sh
➜ go mod vendor
➜ cat vendor/modules.txt
# go build -mod=vendor
```

```sh
➜ go get -d github.com/enescakir/emoji@v0.0.5
# Inconsistent vendoring detected
➜ go mod vendor
```

---

### Структура проекта

```sh
repo/
- file.go
- file_test.go
- go.mod
- go.sum
```

```sh
repo/
- package-a/
  - file.go
  - file_test.go
  - go.mod
  - go.sum
- package-b/...
```

```sh
repo/
- cmd/
  - command-a/
    - main.go
- internal/
  - package-a
  	- file.go
  	- file_test.go
  - package-b/...
- pkg/
  - package-c/
    - file.go
    - file_test.go
    - go.mod
    - go.sum
  - package-d/...
tests/...
```

---





















## ⏰

























---



















## Инструменты **для**



























---

### Инсталяции

```sh
➜ go install [build flags] [packages]
#     main packages $GOBIN=$GOPATH/bin
# non-main packages $GOPATH/pkg/mod or $GOPATH/pkg/$GOOS_$GOARCH

➜ GOBIN=$HOME/bin/ go install
```

```sh
# GOPROXY=""
# GOPROXY=direct
# ...
```

```sh
➜ go install golang.org/x/tools/gopls@latest
➜ go install golang.org/x/tools/gopls@v0.6.4
➜ go install golang.org/x/tools/{gopls,cover}@latest

➜ go clean -i golang.org/x/tools/gopls@v0.6.4
```

```sh
➜ go install ./cmd/...# wildcard
➜ go get golang.org/x/tools/...
```

```sh
➜ go get github.com/pkg/errors # -d
```

```go
// +build ignore
```

Для установки конфигурационных файлов необходимо использовать **Makefile**

- [ ]  **Semantic Versioning**  🏡

---

### Компилирования

```sh
➜ go build -o hello-world hello-world.go # порядок 🔬
# go run hello-world.go
➜ ./hello-world
➜ ls -la hello-world
-rwxr-xr-x 1 creator creator 2008801 Mar 20 17:36 hello-world

➜ file hello-world
hello-world: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), statically linked, Go, ..., not stripped
```

Кроссплатформенная сборка

```sh
➜ env GOOS=target-OS GOARCH=target-architecture go build -o hello-world ./hello-world.go

➜ env GOOS=windows GOARCH=amd64 go build ./hello-world.go
➜ file ./hello-world.go
hello-world.exe: PE32+ executable (console) x86-64 (stripped to external PDB), for MS Windows
```

| Переменная | Список                                                       |
| ---------- | ------------------------------------------------------------ |
| **GOOS**   | **`aix`** `android` **`darwin`** **`dragonfly`** **`freebsd`** `hurd` **`illumos`** **`js`** **`linux`** `nacl` **`netbsd`** **`openbsd`** **`plan9`** **`solaris`** **`windows`** `zos` |
| **GOARCH** | **`amd64`** **`arm64`** `arm64be` **`ppc64`** **`ppc64le`** **`mips64`** **`mips64le`** **`riscv64`** **`s390x`** `sparc64` **`wasm`** |

- [ ] Флаги компиляции и компиляторы 🏡

---

### Анализа

**Linter aggregators**

|  №   | Название                                                     | Описание                                                     | Спецификаторы    |      |
| :--: | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------- | :--: |
|  1   | [deadcode](https://github.com/remyoudompheng/go-misc/tree/master/deadcode) | Errcheck is a program for checking for unchecked errors in go programs... | unused           |  +   |
|  2   | [errcheck](https://github.com/kisielk/errcheck)              | Errcheck is a program for checking for unchecked errors in go programs... | bugs, error      |  +   |
|  3   | [gosimple](https://github.com/dominikh/go-tools/tree/master/simple) | Linter for Go source code that specializes in simplifying a code... | style            |  +   |
|  4   | [govet](https://golang.org/cmd/vet/)                         | Vet examines Go source code and reports suspicious constructs, such as Printf calls... | bugs, metalinter |  +   |
| ...  | ...                                                          | ...                                                          | ...              | ...  |
|  73  | [wsl](https://github.com/bombsimon/wsl)                      | Whitespace Linter - Forces you to use empty lines!           | style            |  -   |

**Introspectors**

```sh
➜ otool -L hello-world
hello-world:
	/usr/lib/libSystem.B.dylib (compatibility version 0.0.0, ...)
➜ go tool nm hello-world 📽️
```

- [ ] Профилирование с помощью **pprof** 🏡

---

### Тестирования

```sh
➜ go test [build/test flags] 
				  [packages] 
			  	[build/test flags & test binary flags]
```

```sh
➜ go test      # local directory mode
➜ go test ./...# package list mode
```

> Files whose names begin with **_** (including **_test.go**) or **.** are ignored

```sh
# testflag
-json
-failfast
-cpu 1,2,4
-run regexp
...
-cpuprofile cpu.out
-memprofile mem.out
-mutexprofile mutex.out
```

```sh
➜ go test -coverprofile=cover.out ./...
➜ go tool cover -func=cover.out
➜ go tool cover -html=cover.out

# -covermode=set|count|atomic
```

```sh
➜ ginkgo ./...
```

- [ ]  **Coverage** одноименных проектов, написанных на разных языках  🏡

---

### Документирования

```go
// Errorf creates a formatted error.
func Errorf(format string, args ...interface{}) error {
  ...
```

Пример использования **doc.go** файла 📽️



```go
// Execer is an optional interface that may be implemented by a Conn.
//
// If a Conn does not implement Execer, the sql package's DB.Exec will
// first prepare a query, execute the statement, and then close the
// statement.
//
// Exec may return ErrSkip.
//
// Deprecated: Drivers should implement ExecerContext instead.
type Execer interface {
	Exec(query string, args []Value) (Result, error)
}
```

```sh
➜ go help doc
➜ gh() { go help $1 | more }
```

```shell
➜ go get golang.org/x/tools/cmd/godoc
```

- [ ] **godoc**  🏡

---

### Отладки

```sh
➜ go install github.com/go-delve/delve/cmd/dlv@latest
```

```sh
# git clone github.com/enescakir/emoji into $GOPATH/src/...
```

```go
import "github.com/enescakir/emoji"
```

```go
module github.com/creator/hello-world
go 1.15
require github.com/enescakir/emoji v1.0.0
```

```sh
➜ ls $GOPATH/pkg/mod/github.com/enescakir/emoji@v1.0.0
```

```shell
➜ go mod edit -replace github.com/enescakir/emoji=$GOPATH/src/github.com/enescakir/emoji
# git clone github.com/enescakir/emoji into $GOPATH/src/...
```

```sh
➜ CGO_ENABLED=0 go build -gcflags "all=-N -l" -o hello-world
➜ dlv --listen=:2345 \
      --headless=true \
      --accept-multiclient \
      --api-version=2 exec ./hello-world
# --log=true \
# --log-output=debugger,debuglineerr,gdbwire,lldbout,rpc
```

- [ ] Отладить различные приложения 🏡

---

### Разработки

Стандартные:

- gopls
- gofmt
- gotype
- godoc
- godex
- godef
- cover
- dlv
- goimports
- gomvpkg
- gorename

Продвинутые:

- Golan**d**

- **vim**-go vs **coc**-go

- go-mode.el

  > It is a complete rewrite of the go-mode that shipped with Go 1.0.3 and before, and was part of Go 1.1 until Go 1.3. Beginning with Go 1.4, editor integration will not be part of the Go distribution anymore, making this repository the canonical place for go-mode.

- VSCode

- [ ] Настроить удобное для себя окружение 🏡

---





















## temlate 📽️





















---






































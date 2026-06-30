# c-http-server

Servidor HTTP construído em C, do zero, com o objetivo de perceber a fundo
como funciona o protocolo HTTP e a camada de sockets POSIX por baixo de
frameworks que normalmente abstraem isto (Spring Boot, etc.).

Projeto pessoal de aprendizagem — sem dependências externas além da
biblioteca padrão e POSIX (`socket`, `bind`, `listen`, `accept`, ...).

## Porquê

- Reforçar C e POSIX depois de algum tempo sem praticar.
- Entender HTTP "por dentro": parsing de request line, headers, status codes.
- Construir algo que liga diretamente à área de telecomunicações/redes.

## Objetivos de aprendizagem

- [ ] Sockets TCP em C (POSIX)
- [ ] Parsing manual de um request HTTP/1.1
- [ ] Modelo de concorrência (threads vs `epoll`/event loop)
- [ ] Servir ficheiros estáticos com os headers corretos
- [ ] Roteamento simples (`GET /caminho` → handler)

## Roadmap / Versões

O progresso está organizado por Milestones e Issues no GitHub. Ver
[TODO.md](./TODO.md) para o detalhe de cada fase.

| Versão | Estado | Descrição |
|--------|--------|-----------|
| v0.1   | 🔲 Por fazer | Aceita ligação TCP, devolve sempre `200 OK` |
| v0.2   | 🔲 Por fazer | Parsing real do request + servir ficheiros estáticos |
| v0.3   | 🔲 Por fazer | Concorrência (threads ou epoll) |
| v0.4   | 🔲 Por fazer | Routing simples por path/método |

## Como correr

```bash
make
./server <porta>
```

(detalhes de build a adicionar conforme o projeto avança)

## Estrutura do projeto

```
.
├── src/
│   ├── main.c
│   ├── http_parser.c
│   ├── http_parser.h
│   └── ...
├── tests/
├── Makefile
├── README.md
└── TODO.md
```

## Notas / referências usadas

- RFC 7230 (HTTP/1.1 Message Syntax and Routing)
- `man 2 socket`, `man 2 bind`, `man 2 listen`, `man 2 accept`
- Beej's Guide to Network Programming

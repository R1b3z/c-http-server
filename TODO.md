# TODO

Lista de tarefas organizadas por versão/fase. Sugestão: cada checkbox
abaixo vira uma Issue no GitHub, agrupada num Milestone com o mesmo nome
da versão (v0.1, v0.2, ...), e arrastada num Project board (To Do / In
Progress / Done).

Regra simples para não perder o foco: só passar à fase seguinte depois de
todas as tarefas da fase atual estarem fechadas e o código fazer commit
com tag (`git tag v0.1`).

---

## v0.1 — Servidor mínimo (TCP bruto)

- [ ] Criar socket TCP (`socket`, `bind`, `listen`)
- [ ] Aceitar uma ligação (`accept`)
- [ ] Ler os bytes recebidos (sem parsing, só imprimir no terminal)
- [ ] Responder sempre com `HTTP/1.1 200 OK` + corpo fixo "Hello"
- [ ] Testar com `curl localhost:<porta>`
- [ ] Makefile básico (`make`, `make clean`)
- [ ] Commit + tag `v0.1`

**Critério de "done":** `curl localhost:8080` devolve sempre 200 OK com
o corpo fixo, sem crash.

---

## v0.2 — Parsing real + ficheiros estáticos

- [ ] Parser da request line (método, path, versão HTTP)
- [ ] Parser de headers (`Host`, `Content-Length`, etc. — guardar em
      estrutura/lista)
- [ ] Mapear `path` pedido para um ficheiro dentro de uma pasta `public/`
- [ ] Devolver 404 se o ficheiro não existir
- [ ] Adicionar headers de resposta corretos (`Content-Type`,
      `Content-Length`)
- [ ] Testar com browser (não só curl) a abrir um `index.html`
- [ ] Commit + tag `v0.2`

**Critério de "done":** consigo abrir `localhost:8080` no browser e ver
uma página estática a carregar corretamente (HTML + CSS + imagem).

---

## v0.3 — Concorrência

- [ ] Decidir abordagem: thread por ligação vs `epoll`/event loop
      (recomendo começar por thread por ligação, é mais simples; `epoll`
      como extensão opcional depois)
- [ ] Implementar e testar múltiplos pedidos simultâneos
      (`ab` ou `wrk` para benchmark simples)
- [ ] Lidar com erros de concorrência (race conditions, fecho de sockets)
- [ ] Commit + tag `v0.3`

**Critério de "done":** o servidor aguenta N pedidos simultâneos sem
bloquear nem crashar (testar com `ab -n 100 -c 10 http://localhost:8080/`).

---

## v0.4 — Routing (opcional, se ainda houver motivação)

- [ ] Estrutura simples de rotas: `(método, path) -> função handler`
- [ ] Pelo menos 2 rotas dinâmicas de exemplo (ex: `GET /time`,
      `POST /echo`)
- [ ] Commit + tag `v0.4`

**Critério de "done":** consigo adicionar uma rota nova só escrevendo
uma função handler, sem mexer no resto do código.

---

## Ideias para depois (não bloqueantes, só para não esquecer)

- [ ] Suporte a HTTPS (TLS) com OpenSSL
- [ ] Logging estruturado para ficheiro
- [ ] Configuração via ficheiro `.conf` em vez de hardcoded

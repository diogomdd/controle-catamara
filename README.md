# Controle Catamarã

PWA de controle de embarques, contas de embarcações, contas Jardas e prestação Jacilene.

## Publicação segura

Antes de publicar uma versão com login:

1. Ativar o provedor **E-mail/senha** no Firebase Authentication.
2. Criar a conta compartilhada que será usada nos celulares autorizados.
3. Criar no Firestore o documento `usuariosAutorizados/UID_DA_CONTA`.
4. Publicar `firestore.rules` com o Firebase CLI.
5. Somente depois publicar `index.html`, `sw.js` e `manifest.json` no GitHub Pages.

As regras recusam qualquer conta que não possua seu UID em `usuariosAutorizados`.

## Dados e segurança

- Cada lançamento conserva as tarifas usadas no dia.
- Exclusões de guias e embarcações são arquivadas em `historicoExclusoes`.
- Backups versão 3 preservam identificadores e podem ser mesclados sem duplicação.
- A restauração usa lotes de até 400 operações e envia o backup antes de remover dados antigos.
- Fechamentos Jardas não aceitam datas futuras.
- Vouchers com mais de cinco dias são divididos em páginas.

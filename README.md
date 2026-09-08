# Braço Forte Reciclagem

Sistema local de controle de compra de materiais (venda/estoque) para reciclagem, com
emissão de recibo em 2 vias e geração de relatórios.

Tudo roda em **um único arquivo** (`index.html`), sem internet, sem instalação e sem
servidor — feito para computador antigo.

## Como usar

1. Abra o arquivo **`index.html`** com um duplo clique (abre no navegador — Chrome, Edge ou Firefox).
2. (Opcional) Crie um atalho dele na área de trabalho.

Os dados ficam guardados **no próprio navegador daquele computador** (armazenamento local).
Não apague os dados do site / histórico do navegador sem antes fazer um backup (veja abaixo).

## Primeiro acesso (ADM)

1. Clique na aba **Administração**.
2. Senha padrão: **`admin`**
3. Em **Segurança**, troque a senha.
4. Em **Materiais e preços** já vêm ~36 materiais cadastrados. Revise os preços e ajuste
   o que precisar (adicionar, renomear, mudar preço, ou desmarcar "Ativo" para esconder).
   Observações sobre o cadastro inicial:
   - **Óleo (por litro)**: o sistema multiplica quantidade × preço, então o operador
     digita os **litros** no campo de peso.
   - **Cobre de 4mm**: nome foi interpretado do original "Cobre de 4•" — renomeie se
     estiver errado.
5. Em **Dados da empresa**, preencha nome, CNPJ, endereço, telefone e o rodapé — isso
   aparece no cabeçalho do cupom.

> Se ao abrir a tela de compra aparecer uma lista antiga de materiais (o navegador
> guardou um teste anterior), limpe os dados do site uma vez: F12 → Application →
> Local Storage → clique com o direito no endereço do arquivo → "Clear".

## Operação (aba Compra)

1. **Escolha o material** tocando no botão dele (todos ficam à vista, em ordem
   alfabética). O botão fica verde com um ✓.
2. Digite o **peso em kg** (aceita vírgula ou ponto). O sistema mostra a conta pronta.
   Tecle **Enter** ou clique em **Adicionar**.
3. A linha entra na lista e acende verde. O material continua selecionado — é só digitar
   o próximo peso, ou tocar em outro material.
4. O **TOTAL** aparece grande na barra escura embaixo, sempre visível.
5. (Opcional) Abra **Dados do cliente e forma de pagamento** para preencher nome,
   documento, placa, pagamento (botões) e observação.
6. Clique **Imprimir e finalizar** — salva a compra e manda as 2 vias para a impressora
   (via RECICLAGEM + linha de corte + via CLIENTE).
   - **Finalizar sem imprimir**: só registra.
   - **Reimprimir última** / **Cancelar compra**: links abaixo da lista.

## Impressora térmica (cupom 80mm)

O layout já é feito para bobina de **80mm**. Na janela de impressão do navegador:

- Impressora: selecione a térmica.
- Margens: **Nenhuma**.
- Tamanho do papel: 80mm x recibo (ou "72mm" / rolo), conforme o driver.
- Desmarque "Cabeçalhos e rodapés".
- Marque "Gráficos em segundo plano" se a linha de corte não aparecer.

Dica: no Chrome/Edge dá para marcar "Imprimir usando a caixa de diálogo do sistema" e
salvar essas configurações como padrão da impressora.

## Backup / nuvem

Na aba **Administração > Backup**:

- **Exportar TUDO (JSON)**: gera `reciclagem_backup_AAAA-MM-DD_HHMM.json` com **compras +
  materiais + configuração + registro de alterações**. **Suba esse arquivo na nuvem**
  (Google Drive, OneDrive, etc.).
  Recomendado fazer no fim de cada expediente.
- Um aviso vermelho mostra quantas compras ainda não entraram em nenhum backup.
- **Importar / restaurar JSON**: em outro computador ou após formatar, importe o último
  backup (opção `SUBSTITUIR` para restaurar tudo, `MESCLAR` para juntar compras).

## Relatórios

Aba **Administração > Relatórios**: escolha o período e clique **Gerar**. Mostra total de
compras, peso e valor pago, resumo por material e lista das compras. Dá para exportar em
**CSV (abre no Excel)** ou **JSON** do período.

## Registro de alterações (log)

Aba **Administração > Registro de alterações**. Toda mudança administrativa fica gravada
com data e hora:

- preço alterado (ex: *"Preço alterado: Papelão de R$ 2,40 para R$ 5,60 por kg"*)
- material cadastrado / renomeado / desativado / removido
- lista de materiais restaurada para o padrão
- compra apagada (ex: *"Compra Nº 03 de 05/09/2026 16:20 (R$ 214,80) apagada"*)
- senha de administração alterada
- dados da empresa alterados
- backup importado

O log fica salvo junto (`bfr_log`) e **entra no "Exportar TUDO"**. Dá também para exportar
só o log (**Exportar log completo (JSON)**). A tela mostra os 100 registros mais recentes;
o arquivo tem todos.

## Manutenção

- **Apagar compras antigas**: remove do computador compras anteriores a uma data. Só use
  depois de confirmar que o backup na nuvem está salvo.

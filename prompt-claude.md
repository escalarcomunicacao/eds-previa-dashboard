# Atualizar o dashboard do EDS em /painel

Você está no repositório escalarcomunicacao/NovoGerenciador. Implemente a atualização do dashboard de rede de telas no ambiente de desenvolvimento do EDS. Use a demonstração interativa e os prints desta issue como referência de layout e interação. Os números, nomes e datas da demonstração são fictícios. Na implementação, use as fontes reais disponíveis para a conta autenticada.

## Fluxo do repositório

Leia AGENTS.md, CLAUDE.md, .github/copilot-instructions.md e as instruções especializadas aplicáveis ao painel. Trabalhe no checkout principal e confira com git branch --show-current que a branch é master. Faça o commit direto na master e informe o hash para revisão. Sem branch adicional, worktree ou pull request. Preserve trabalhos locais de outras pessoas e use dev para validar a entrega.

## Layout

Atualize a rota existente /painel e mantenha a navegação do EDS. Use a composição da prévia, com os cinco cartões no topo e as seções Conexão das telas, Pontos que exigem atenção, Veiculação por anúncio ou comunicado, Entrega das publicações, O que está passando agora, Próximos 14 dias, Plano e consumo, Biblioteca de mídias, Unidades e equipamentos e Serviços contratados. Preserve os recursos e permissões da tela atual. Quando uma informação estiver indisponível ou fora das permissões da conta, use o estado apropriado do EDS e informe na entrega quais seções ficaram nessa condição.

## Cartões e modais

- Pontos cadastrados abre os players cadastrados acessíveis na conta.
- No ar abre a lista de players no ar.
- Baixando conteúdo abre a lista de players baixando conteúdo.
- Exigem atenção abre os players classificados como exigindo atenção pelo EDS.
- Sem programação abre a lista de players sem programação válida.
- Reutilize o padrão de modais do painel, incluindo a convenção de busca e paginação e os links existentes para o detalhe do player quando permitido. Calcule o total exibido e a lista a partir do mesmo recorte, com a mesma regra de classificação e de acesso. Entre as categorias, preserve as regras de status do EDS para casos que possam se sobrepor.
- Exiba nome, ID, local, situação e último contato conforme os dados disponíveis. Busque por nome, ID e local antes de paginar. Diferencie lista vazia de busca sem resultado. Cartões com total zero também abrem o modal.
- Valide abertura pelo teclado, fechamento pelo botão e por Esc, retorno de foco e uso no celular.

## Conexão das telas

- Retire os seletores globais de local, grupo e período do cabeçalho do dashboard. Posicione o seletor no próprio cartão Conexão das telas.
- Disponibilize 30, 15, 7 e 3 dias, com 30 selecionado na primeira abertura.
- Calcule a janela atual com N dias completos até o dia anterior, de acordo com o fuso adotado pelo painel. Compare com os N dias imediatamente anteriores à janela atual. As janelas são contíguas e sem sobreposição. Por exemplo, em 26/11/2026, a opção de 7 dias compara 19–25/11 com 12–18/11.
- Mostre as datas das duas janelas, as duas séries diárias de conexão em horário comercial, as respectivas médias, a diferença em pontos percentuais e a contagem dos dias do período atual abaixo da meta de 95%. Preserve os critérios existentes de horário comercial e indique a falta de histórico conforme o padrão do painel.
- Alterar o período atualiza só Conexão das telas. Entrega das publicações usa sua janela de 7 dias e Próximos 14 dias usa sua própria janela. A seleção de peça em Veiculação também tem controle próprio.

## Referências e entrega

Prévia funcional com as interações aprovadas:
https://escalarcomunicacao.github.io/eds-previa-dashboard/

Consulte PainelController, os serviços PainelConexaoService e PainelModalService e as views atuais de resources/views/pages/painel. Use os prints do dashboard completo e dos cinco modais anexados à issue para conferir o resultado.

Valide em dev os quatro recortes, o isolamento do filtro, as cinco listas por categoria, a busca além da primeira página, a paginação, o estado vazio, as permissões e o layout de desktop e celular. Ao concluir, informe o hash do commit na master e os cenários verificados.

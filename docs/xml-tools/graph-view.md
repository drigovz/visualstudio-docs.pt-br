---
title: Exibição do gráfico do Designer de Esquema XML
description: Saiba mais sobre a exibição de gráfico no designer de esquema XML que fornece uma representação gráfica dos nós de esquema global e as relações entre os nós.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee6abff7accf5e1990792b52f1fdf6a013edd0f9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046000"
---
# <a name="graph-view"></a>Exibição de gráfico

A exibição do gráfico fornece uma representação gráfica de nós globais do esquema e relações entre os nós. Observe que a exibição do gráfico não permite que você alterar o layout do esquema definido na superfície de design. A exibição do gráfico também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.

A imagem a seguir mostra a visualização de gráfico com seis nós globais na superfície de design.

![Exibição do gráfico do Designer de Esquema XML](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Superfície de design

A superfície de design da exibição de gráfico exibe o conteúdo do [espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md). Se o workspace contém quaisquer nós globais do conjunto de esquema, os nós são mostrados na superfície de design do modo de gráfico e as setas são desenhadas entre os nós que possuem relações.

Clicar duas vezes em um nó no modo de exibição de gráfico abrirá o editor de XML.

Para excluir os nós selecionados do espaço de trabalho, use a barra de ferramentas do XSD designer ou a tecla **delete** .

Se a superfície de design estiver em branco, o editor de XML, o **XML Schema Explorer** e a marca d' água serão mostrados. A *marca d' água* é uma lista de links para todas as exibições do designer XSD.

![Designer XSD; Exibição do gráfico](../xml-tools/media/xsdgraphviewwatermark.gif)

Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”

## <a name="breadcrumb-bar"></a>Barra de navegação estrutural

A barra de rastreamento na parte inferior do modo de figura a seguir mostra onde o nó selecionado é localizado no conjunto de esquema. Se vários itens são selecionados, a barra de rastreamento será em branco.

## <a name="context-right-click-menu"></a>Menu de contexto (clique com o botão direito do mouse)

A tabela a seguir descreve as opções que estão disponíveis para todos os nós na superfície de design do modo de gráfico.

|Opção|Descrição|
|-|-----------------|
|**Apresentação em XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Apresentação no modo de gráfico**|Alterna para o modo de exibição gráfico (desativada).|
|**Gerencia o exemplo XML**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**O workspace claro**|Limpa o workspace e a superfície de design.|
|**Remova de workspace**|Removes selecionou nós de workspace e da superfície de design.|
|**Remova todos com exceção de seleção de workspace**|Remove os nós que não são selecionados de workspace e da superfície de design.|
|**Exportar diagrama como imagem**|Salva a superfície de design para um arquivo XPS.|
|**Selecionar tudo**|Selecionar todos os nós na superfície de design.|
|**Exibir Código**|Abre o arquivo que contém o nó selecionado no editor de XML. O item selecionado no **XML Schema Explorer** também é selecionado no editor de XML.|
|**Janela Propriedades**|Abre a janela **Propriedades** (se ainda não estiver aberta). Esta janela exibe informações sobre o nó.|

Além das opções comuns descritas anterior, o menu de contexto para elementos globais também tem as seguintes opções:

|Opção|Descrição|
|-|-----------------|
|**Adicionar Definição de Tipo**|Adiciona o tipo base no diagrama.|
|**Adicionar Todas as Referências**|Adiciona todos os nós que se referem ao elemento e desenha setas para indicar relações entre eles.|
|**Adicionar Membros do Grupo de Substituição**|Adiciona todos os membros do grupo de substituição. Essa opção aparece na exibição se o elemento é o início ou membro de um grupo de substituição.|
|**Gerencia o exemplo XML**|Gerencia um arquivo XML de exemplo para o elemento global.|

Além das opções comuns descritas anterior, o menu de contexto para tipos complexos simples e globais globais também tem as seguintes opções:

|Opção|Descrição|
|-|-----------------|
|**Adicione o tipo base**|Se o tipo selecionado é derivado de um tipo global, adiciona o tipo base do tipo selecionado.|
|**Adicionar Todas as Referências**|Adiciona todas as referências de tipo selecionado. Isso inclui os elementos e atributos do tipo selecionado, e tipos derivados do tipo selecionado.|
|**Adicionar Todos os Tipos Derivados**|Adiciona todos os tipos que direta e indiretamente são derivados do tipo selecionado.|
|**Adicionar Todos os Ancestrais**|Adiciona todos os tipos de base pai ().|

Além das opções comuns descritas anterior, o menu de contexto para grupos globais e grupos de atributo também tem as seguintes opções:

|Opção|Descrição|
|-|-----------------|
|**Adicionar Todas as Referências**|Adiciona todos os nós que se referem ao grupo e desenha setas para indicar relações entre eles.|
|**Adicionar Todos os Membros**|Adiciona todos os membros do grupo e desenha setas para indicar relações entre eles.|

No addtion em padrões comuns descritas anterior, o menu de contexto para atributos globais também tem as seguintes opções:

|Opção|Descrição|
|-|-----------------|
|**Adicionar Todas as Referências**|Adiciona todos os nós que se referem ao grupo e desenha setas para indicar relações entre eles.|

## <a name="properties-window"></a>Janela de Propriedades

Use o menu de contexto (clique com o botão direito do mouse) para abrir inicialmente a janela **Propriedades** . Por padrão, a janela **Propriedades** é exibida no canto inferior direito do Visual Studio. Quando você clica em um nó que é processado no modo de exibição de modelo de conteúdo, as propriedades desse nó serão exibidas na janela **Propriedades** .

## <a name="xsd-toolbar"></a>Barra de ferramentas XSD

Os seguintes botões da barra de ferramentas XSD são ativados quando a exibição do gráfico está ativo.

![Barra de ferramentas do Designer de Esquema XML](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Opção|Descrição|
|-|-----------------|
|**Mostrar Exibição Inicial**|Alterna para o [modo de exibição de início](../xml-tools/start-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl** + **1** .|
|**Mostrar Exibição de Modelo de Conteúdo**|Alterna para a [exibição do modelo de conteúdo](../xml-tools/content-model-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl** + **2** .|
|**Mostrar Exibição de Gráfico**|Alterna para o [modo de exibição de gráfico](../xml-tools/graph-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl** + **3** .|
|**O workspace claro**|Limpa o workspace e a superfície de design.|
|**Remova de workspace**|Removes selecionou nós de workspace e da superfície de design.|
|**Remova todos com exceção de seleção de workspace**|Remove os nós que não são selecionados de workspace e da superfície de design. Essa opção é ativada no modo do modelo de conteúdo e no modo de gráfico.|
|**Da esquerda para a direita**|Altera o layout no modo de gráfico a uma representação hierárquica esquerda para a direita de nós. Essa opção pode ser acessada usando o atalho de **Alt** teclado: + **seta para a direita** Alt.|
|**Da direita para a esquerda**|Altera o layout no modo de gráfico a uma representação hierárquica da direita para a esquerda de nós. Essa opção pode ser acessada usando o atalho de teclado: **ALT** + **seta para a esquerda** .|
|**De Cima para Baixo**|Altera o layout no modo de gráfico a uma representação hierárquica de cima para baixo de nós. Essa opção pode ser acessada usando o atalho de teclado: **ALT** + **seta para baixo** .|
|**De baixo para cima**|Altera o layout no modo de gráfico a uma representação hierárquica de parte inferior-à- parte superior dos nós. Essa opção pode ser acessada usando o atalho de **Alt** teclado: + **seta para cima** Alt.|

## <a name="panscroll"></a>Bandeja/rolagem

Você pode deslocar a superfície de design usando as barras de rolagem ou mantendo a tecla **Ctrl** pressionada enquanto clica e arrasta o mouse. Quando você filtra a superfície de design usando o clique e o arrastar, o cursor será alterado a quatro setas cruzadas apontando em quatro direções.

## <a name="undoredo"></a>Desfazer/refazer

Desfazer/refaz o recurso é habilitado no modo de gráfico para as seguintes ações:

- Adicionando um único nó arrastando e soltando-se.

- Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer ou em consultas de exibição de Início.

- Excluindo única ou mais nós.

## <a name="zoom"></a>Zoom

O zoom está disponível no canto inferior direito do modo de gráfico.

O zoom pode ser controlado das seguintes maneiras:

- Segurando a tecla **Ctrl** e girando a roda do mouse quando o mouse estiver passando pela superfície de exibição do gráfico.

- Usando o controle deslizante. O controle deslizante mostra o nível atual de zoom.

O controle deslizante de zoom é opaco quando você o seleciona, passa o mouse sobre ele ou usa **Ctrl** com a roda do rato para aplicar zoom; em outras ocasiões, ele é transparente.

## <a name="xml-editor-integration"></a>Integração do editor de XML

Você pode alternar entre o modo de exibição de gráfico e o editor de XML clicando em um nó e usando o menu de contexto do código de exibição (clique com o botão direito do mouse).

Se você fizer alterações no conjunto de esquema no editor de XML, as alterações serão sincronizadas no modo de exibição de gráfico. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Veja também

- [Design Surface](../xml-tools/xml-schema-designer-workspace.md)

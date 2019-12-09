---
title: Exibição do modelo de conteúdo do Designer de Esquema XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67453571963ae22910842be0021e008632942de5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661533"
---
# <a name="content-model-view"></a>O modo do modelo de conteúdo

A exibição do modelo de conteúdo fornece uma representação gráfica de nós locais e globais de esquema e seus componentes, de incluir simples e tipos complexos, de elementos, grupos de modelo, de atributos, e de grupos de atributo. Comentários e instruções de processamento XML não podem ser exibidos no modo do modelo de conteúdo. A exibição do modelo de conteúdo contém dois painéis: um painel do **espaço de trabalho** que contém uma lista dos nós no espaço de trabalho do [Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)e a superfície de design onde você pode ver o modelo de conteúdo dos nós de esquema selecionados no **espaço de trabalho** painel. A exibição do modelo de conteúdo também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.

Na imagem a seguir, o painel de **espaço de trabalho** contém seis nós de esquema. O nó `purchaseOrder` é selecionado no painel do **espaço de trabalho** e é exibido na superfície de design.

![Exibição do modelo de conteúdo do Designer de Esquema XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Painel do espaço de trabalho

Depois de adicionar nós ao espaço de trabalho, a lista de nós aparecerá no painel do **espaço de trabalho** do modo de exibição de modelo de conteúdo. Quando você seleciona nós no painel do **espaço de trabalho** , eles aparecem na superfície de design da exibição do modelo de conteúdo. Para excluir nós do espaço de trabalho, use a barra de ferramentas do designer XSD, o menu de **espaço de trabalho** , clique com o botão direito do mouse ou a tecla **delete** .

Para obter informações sobre como adicionar nós, consulte a seção "adicionando nós ao espaço de trabalho" no [espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Superfície de design

Quando um nó é selecionado no painel do **espaço de trabalho** , ele é adicionado à superfície de design da exibição do modelo de conteúdo, na qual você pode exibir os detalhes do nó.

O modelo de conteúdo de um nó é representado por uma árvore gráfico expansível com elementos e atributos que aparecem como nós de árvore. Por padrão, somente um nível é expandido. Outras informações, como compositores, nomes de tipo, grupos, e outros contêineres é colocada em uma barra vertical (quando expandido) ao longo de elementos e atributos que incluem. Quando você clica duas vezes em uma barra vertical, transformações horizontal e recolhe de árvore. Quando você clica duas vezes em uma barra horizontal e vertical, transformações a árvore expande. Selecionar a barra vertical seleciona todos os nós no contêiner. Os expansores aparecem à direita de um nó se um elemento pode ser expandido ou recolhido.

Se a superfície de design estiver em branco, o editor de XML, o **XML Schema Explorer**e a marca d' água serão mostrados. A *marca d' água* é uma lista de links para todas as exibições do designer XSD. Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”

## <a name="breadcrumb-bar"></a>Barra de navegação estrutural

A barra de rastreamento na parte inferior do modo de modelo de conteúdo mostra onde o nó selecionado é localizado no conjunto de esquema.

## <a name="context-menus"></a>Menus de contexto

Quando você clica com o botão direito do mouse em um item na superfície de design ou no painel do **espaço de trabalho** , um menu de contexto é exibido. A tabela a seguir descreve as opções que estão disponíveis para a superfície de design do modo de modelo de conteúdo.

|Opção|Descrição|
|-|-----------------|
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Mostrar no modo de exibição de gráfico**|Alterna a O modo de gráfico.|
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Mostrar documentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|
|**Exportar diagrama como imagem**|Salva a superfície de design para um arquivo XPS.|
|**Exibir Código**|Abre o arquivo que contém o nó selecionado no editor de XML. O item selecionado no **XML Schema Explorer** também é selecionado no editor de XML.|
|**Janela Propriedades**|Abre a janela **Propriedades** (se ainda não estiver aberta). Esta janela exibe informações sobre o nó.|

A tabela a seguir descreve as opções que estão disponíveis para o painel do **espaço de trabalho** .

|Opção|Descrição|
|-|-----------------|
|**Mostrar no XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Mostrar no modo de exibição de gráfico**|Alterna para representar graficamente a exibição.|
|**Limpar espaço de trabalho**|Limpa o workspace e a superfície de design.|
|**Remover do espaço de trabalho**|Removes selecionou nós de workspace e da superfície de design.|
|**Remover tudo, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de workspace e da superfície de design.|
|**Gerar XML de exemplo**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Selecionar tudo**|Seleciona todos os nós no painel do **espaço de trabalho** .|
|**Exibir Código**|Abre o arquivo que contém o nó selecionado no editor de XML. O item selecionado no **XML Schema Explorer** também é selecionado no editor de XML.|
|**Janela Propriedades**|Abre a janela **Propriedades** (se ainda não estiver aberta). Esta janela exibe informações sobre o nó.|

## <a name="properties-window"></a>Janela de Propriedades

Use o menu de clique com o botão direito do mouse (contexto) para abrir inicialmente a janela **Propriedades** . Por padrão, a janela **Propriedades** é exibida no canto inferior direito do Visual Studio. Quando você clica em um nó que é processado no modo de exibição de modelo de conteúdo, as propriedades desse nó são exibidas na janela **Propriedades** .

## <a name="xsd-designer-toolbar"></a>Barra de ferramentas do designer XSD

Os seguintes botões da barra de ferramentas do designer XSD são ativados quando a exibição do modelo de conteúdo está ativo.

![Barra de ferramentas do Designer de Esquema XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opção|Descrição|
|-|-----------------|
|**Mostrar exibição inicial**|Alterna para o [modo de exibição de início](../xml-tools/start-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl** +**1**.|
|**Mostrar exibição do modelo de conteúdo**|Alterna para a [exibição do modelo de conteúdo](../xml-tools/content-model-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl** +**2**.|
|**Mostrar exibição de gráfico**|Alterna para o [modo de exibição de gráfico](../xml-tools/graph-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl** +**3**.|
|**Limpar espaço de trabalho**|Limpa o workspace e a superfície de design.|
|**Remover do espaço de trabalho**|Removes selecionou nós de workspace e da superfície de design.|
|**Remover tudo, exceto a seleção do espaço de trabalho**|Remove os nós que não são selecionados de workspace e da superfície de design.|
|**Mostrar documentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|

## <a name="panscroll"></a>Bandeja/rolagem

Você pode deslocar a superfície de design usando as barras de rolagem ou mantendo a tecla **Ctrl** pressionada enquanto clica e arrasta o mouse. Quando você panorâmica a superfície de design usando clicar e arrastar, o cursor muda para quatro setas cruzadas apontando para quatro direções.

## <a name="undoredo"></a>Desfazer/refazer

Desfazer/refaz o recurso é habilitado no modo de modelo de conteúdo para as seguintes ações:

- Adicionando um único nó arrastando e soltando-se.

- Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer.

- Adicionando a exibição de nós do início.

- Excluindo única ou mais nós.

## <a name="zoom"></a>Aplicar Zoom

O zoom está disponível no canto inferior direito da exibição do modelo de conteúdo.

O zoom pode ser controlado das seguintes maneiras:

- Segurando a tecla **Ctrl** e girando a roda do mouse quando o mouse estiver passando pela superfície de exibição do modelo de conteúdo.

- Usando o controle deslizante. O controle deslizante mostra o nível atual de zoom.

O controle deslizante de zoom é opaco quando você o seleciona, passa o mouse sobre ele ou usa **Ctrl** com a roda do rato para aplicar zoom; em outras ocasiões, ele é transparente.

## <a name="xml-editor-integration"></a>Integração do editor de XML

Você pode alternar entre o **Designer XSD** e o editor de XML usando o menu de clique com o botão direito do mouse (contexto).

Se você fizer alterações no conjunto de esquema no editor de XML, as alterações serão sincronizadas na exibição do modelo de conteúdo. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Consulte também

- [O workspace do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)
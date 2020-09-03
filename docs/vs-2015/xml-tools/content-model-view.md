---
title: Exibição do modelo de conteúdo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47f4703b90446dc615df350ee0641678996196c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657539"
---
# <a name="content-model-view"></a>O modo do modelo de conteúdo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição do modelo de conteúdo fornece uma representação gráfica de nós locais e globais de esquema e seus componentes, de incluir simples e tipos complexos, de elementos, grupos de modelo, de atributos, e de grupos de atributo. Comentários e instruções de processamento XML não podem ser exibidos no modo do modelo de conteúdo. A exibição do modelo de conteúdo contém dois painéis: um painel do **espaço de trabalho** que contém uma lista dos nós no espaço de trabalho do [Designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)e a superfície de design onde você pode ver o modelo de conteúdo dos nós de esquema selecionados no painel do **espaço de trabalho** . A exibição do modelo de conteúdo também inclui a barra de ferramentas do designer de esquema XML e a barra de rastreamento.

 Na figura a seguir, o painel de workspace contém seis nós de esquema. O nó de `purchaseOrder` é selecionado no painel de Workpace e exibido na superfície de design.

 ![Exibição do modelo de conteúdo do Designer de Esquema XML](../xml-tools/media/xsddesigner-contentmodelview.gif "XSDDesigner_ContentModelView")

## <a name="workspace-panel"></a>Painel de workspace
 Depois de adicionar nós ao espaço de trabalho, a lista de nós aparecerá no painel do **espaço de trabalho** do modo de exibição de modelo de conteúdo. Quando você seleciona nós no painel do **espaço de trabalho** , eles aparecem na superfície de design da exibição do modelo de conteúdo. Para excluir nós do workpsace, use a barra de ferramentas do designer XSD, o menu de contexto do painel do **espaço de trabalho** ou a tecla Delete.

 Para obter informações sobre como adicionar nós, consulte a seção "adicionando nós ao espaço de trabalho" no [espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>A superfície de design
 Quando um nó é selecionado no painel de workspace, ele é adicionado para a superfície de design do modo de modelo de conteúdo onde você pode exibir os detalhes do nó.

 O modelo de conteúdo de um nó é representado por uma árvore gráfico expansível com elementos e atributos que aparecem como nós de árvore. Por padrão, somente um nível é expandido. Outras informações, como compositores, nomes de tipo, grupos, e outros contêineres é colocada em uma barra vertical (quando expandido) ao longo de elementos e atributos que incluem. Quando você clica duas vezes em uma barra vertical, transformações horizontal e recolhe de árvore. Quando você clica duas vezes em uma barra horizontal e vertical, transformações a árvore expande. Selecione a barra vertical selecionar todos os nós do contêiner. Os expansores aparecerão no direito de um nó se um elemento pode ser expandido ou recolhido.

 Se a superfície de design está em branco, o editor XML, XML Schema Explorer, e a marca de agua são mostrados. A *marca d' água* é uma lista de links para todas as exibições do designer XSD. Se o esquema tem erros, o seguinte texto é exibido no fim da lista: “Use Lista de erros para exibir e corrigir erros no conjunto.”

## <a name="breadcrumb-bar"></a>Barra de rastreamento
 A barra de rastreamento na parte inferior do modo de modelo de conteúdo mostra onde o nó selecionado é localizado no conjunto de esquema.

## <a name="context-menus"></a>Menus de contexto
 Quando você clica com o botão direito do mouse em um item na superfície de design ou no painel de workspace, um menu de contexto aparece. A tabela a seguir descreve as opções que estão disponíveis para a superfície de design do modo de modelo de conteúdo.

|Opção|Descrição|
|------------|-----------------|
|**Apresentação em XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Apresentação no modo de gráfico**|Alterna a O modo de gráfico.|
|**Gerencia o exemplo XML**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Documentação de apresentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|
|**Diagrama de exportação como a imagem…**|Salva a superfície de design para um arquivo XPS.|
|**Exibir Código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado em XML Schema Explorer também será selecionado no editor XML.|
|**Janela Propriedades**|Abre a janela **Propriedades** (se ainda não estiver aberta). Esta janela exibe informações sobre o nó.|

 A tabela a seguir descreve as opções que estão disponíveis para o painel de workspace.

|Opção|Descrição|
|------------|-----------------|
|**Apresentação em XML Schema Explorer**|Coloca o foco no esquema Explorer e ressalta o nó do esquema.|
|**Apresentação no modo de gráfico**|Alterna para representar graficamente a exibição.|
|**O workspace claro**|Limpa o workspace e a superfície de design.|
|**Remova de workspace**|Removes selecionou nós de workspace e da superfície de design.|
|**Remova todos com exceção de seleção de workspace**|Remove os nós que não são selecionados de workspace e da superfície de design.|
|**Gerencia o exemplo XML**|Disponível somente para os elementos globais. Gerencia um arquivo XML de exemplo para o elemento global.|
|**Selecionar tudo**|Selecionar todos os nós no painel de workspace.|
|**Exibir Código**|Abre o arquivo que contém o nó selecionado no editor XML. O item selecionado em XML Schema Explorer também será selecionado no editor XML.|
|**Janela Propriedades**|Abre a janela **Propriedades** (se ainda não estiver aberta). Esta janela exibe informações sobre o nó.|

## <a name="properties-window"></a>Janela Propriedades
 Use o menu de contexto para abrir inicialmente a janela **Propriedades** . Por padrão, a janela **Propriedades** é exibida no canto inferior direito do Visual Studio. Quando você clica em um nó que é processado no modo de exibição de modelo de conteúdo, as propriedades desse nó serão exibidas na janela **Propriedades** .

## <a name="xsd-designer-toolbar"></a>Barra de ferramentas do designer XSD
 Os seguintes botões da barra de ferramentas do designer XSD são ativados quando a exibição do modelo de conteúdo está ativo.

 ![Barra de ferramentas do Designer de Esquema XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")

|Opção|Descrição|
|------------|-----------------|
|**Mostrar Exibição Inicial**|Alterna para o [modo de exibição de início](../xml-tools/start-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl + 1**.|
|**Mostrar Exibição de Modelo de Conteúdo**|Alterna para a [exibição do modelo de conteúdo](../xml-tools/content-model-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl + 2**.|
|**Mostrar Exibição de Gráfico**|Alterna para o [modo de exibição de gráfico](../xml-tools/graph-view.md). Este modo de exibição pode ser acessado usando o atalho de teclado: **Ctrl + 3**.|
|**O workspace claro**|Limpa o workspace e a superfície de design.|
|**Remova de workspace**|Removes selecionou nós de workspace e serface de design.|
|**Remova todos com exceção de seleção de workspace**|Remove os nós que não são selecionados de workspace e serface de design.|
|**Documentação de apresentação**|Mostra ou de anotação/documentação de oculta conteúdo do nó.|

## <a name="panscroll"></a>Bandeja/rolagem
 Você pode filtrar a superfície de design usando barras de rolagem ou mantendo a tecla CTRL quando você clique e arraste o mouse. Quando você filtra a superfície de design usando o clique e o arrastar, o cursor será alterado a quatro setas cruzadas apontando em quatro direções.

## <a name="undoredo"></a>Desfazer/refazer
 Desfazer/refaz o recurso é habilitado no modo de modelo de conteúdo para as seguintes ações:

- Adicionando um único nó arrastando e soltando-se.

- Adicionando mais nós da janela de resultados de pesquisa no esquema Explorer.

- Adicionando a exibição de nós do início.

- Excluindo única ou mais nós.

## <a name="zoom"></a>Zoom
 O zoom está disponível no canto inferior direito da exibição do modelo de conteúdo.

 O zoom pode ser controlado das seguintes maneiras:

- Mantendo a tecla CTRL e girar o mouse rode quando o mouse está sobre a superfície de exibição do modelo de conteúdo.

- Usando o controle deslizante. O controle deslizante mostra o nível atual de zoom.

  O controle deslizante de zoom é opaco ao selecionar, o passa sobre ele, ou utiliza o CTRL com a roda do mouse para aplicar zoom; em quaisquer outros vezes, é transparente.

## <a name="xml-editor-integration"></a>Integração de editor XML
 Você pode alternar para frente e para trás entre o designer XSD e o editor XML usando o menu de contexto.

 Se você alterar o esquema definido no editor XML as alterações serão sincronizadas no modo de modelo de conteúdo. Para obter mais informações, consulte [integração com o editor de XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Consulte Também
 [Espaço de trabalho do designer de esquema XML](../xml-tools/xml-schema-designer-workspace.md)

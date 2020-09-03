---
title: Janela Propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662079"
---
# <a name="properties-window"></a>Janela Propriedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta janela para exibir e alterar as propriedades de tempo de design e os eventos dos objetos selecionados localizados em editores e designers. Você também pode usar a janela **Propriedades** para editar e exibir as propriedades do arquivo, do projeto e da solução. Você pode encontrar a janela **Propriedades** no menu **Exibir**. Também pode abri-la pressionando F4 ou digitando **Propriedades** na janela **Início Rápido**.

 A janela **Propriedades** exibe tipos diferentes de campos de edição, dependendo das necessidades de uma propriedade em particular. Esses campos de edição incluem caixas de edição, listas suspensas e links a caixas de diálogo do editor personalizado. As propriedades mostradas em cinza são somente leitura.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 Nome do objeto lista o objeto ou objetos selecionados no momento. Somente objetos do editor ou designer ativo ficam visíveis. Quando você seleciona vários objetos, somente as propriedades comuns a todos os objetos selecionados são exibidas.

 Categorizado lista todas as propriedades e valores de Propriedade do objeto selecionado, por categoria. Você pode recolher uma categoria para reduzir o número de propriedades visíveis. Ao expandir ou recolher uma categoria, você vê um sinal de mais (+) ou de menos (-) à esquerda do nome da categoria. As categorias são listadas em ordem alfabética.

 Alfabeticamente classifica todas as propriedades e eventos de tempo de design de objetos selecionados. Para editar uma propriedade não esmaecida, clique na célula à direita e insira as alterações.

 Páginas de Propriedades exibe a caixa de diálogo **páginas de propriedades** ou o **Designer de projeto** para o item selecionado. Páginas de Propriedades exibem um subconjunto, as mesmas ou um superconjunto das propriedades disponíveis na janela **Propriedades**. Use esse botão para exibir e editar propriedades relacionadas à configuração ativa do projeto.

 Propriedades exibe as propriedades de um objeto. Muitos objetos também têm eventos que podem ser exibidos usando a janela **Propriedades**.

 Classificar por Propriedade grupos de origem Propriedades por origem, como herança, estilos aplicados e associações. Disponível somente ao editar arquivos XAML no designer.

 Eventos exibe os eventos de um objeto.

> [!NOTE]
> Esse controle de barra de ferramentas da janela **Propriedades** só está disponível quando um formulário ou designer de controle está ativo no contexto de um projeto [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Ao editar arquivos XAML, os eventos são exibidos em uma guia separada da janela Propriedades.

 Mensagens lista todas as mensagens do Windows. Permite adicionar ou excluir funções especificadas do manipulador para as mensagens fornecidas para a classe selecionada.

> [!NOTE]
> Esse controle de barra de ferramentas da janela **Propriedades** está disponível somente quando **Modo de Exibição de Classe** é a janela ativa no contexto de um projeto [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 Substituições lista todas as funções virtuais da classe selecionada e permite que você adicione ou exclua funções de substituição.

> [!NOTE]
> Esse controle de barra de ferramentas da janela **Propriedades** está disponível somente quando **Modo de Exibição de Classe** é a janela ativa no contexto de um projeto [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 O painel Descrição mostra o tipo de propriedade e uma breve descrição da propriedade. Você pode ativar e desativar a descrição da propriedade usando o comando Descrição no menu de atalho.

> [!NOTE]
> Esse controle de barra de ferramentas da janela **Propriedades** não está disponível ao editar arquivos XAML no designer.

 A exibição de miniatura mostra uma representação visual do elemento atualmente selecionado ao editar arquivos XAML no designer.

 A pesquisa fornece uma função de pesquisa para propriedades e eventos ao editar arquivos XAML no designer. A caixa de pesquisa responde a pesquisas de palavras parciais e atualiza os resultados da pesquisa à medida que você digita.

## <a name="see-also"></a>Consulte Também
 [Referência de propriedades do projeto](../../ide/reference/project-properties-reference.md) [Personalizando layouts de janela](../../ide/customizing-window-layouts-in-visual-studio.md)

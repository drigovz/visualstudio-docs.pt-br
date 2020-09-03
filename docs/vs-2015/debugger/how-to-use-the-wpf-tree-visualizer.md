---
title: 'Como: usar o Visualizador de árvore do WPF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825431"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Como usar o Visualizador de Árvore WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o visualizador de árvore do WPF para explorar a árvore visual de um objeto do WPF e exibir as propriedades de dependência do WPF para os objetos contidos nessa árvore. Para obter mais informações sobre árvores visuais, consulte [árvores no WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Ao abrir o Visualizador de árvore do WPF, você verá dois painéis: a **árvore visual** à esquerda e as **Propriedades do** _painel nome_**:**_tipo_ à direita. Selecione qualquer objeto no painel de **árvore visual** e as **Propriedades do** painel _nome_**:**_tipo_ serão atualizadas automaticamente para mostrar as propriedades desse objeto.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Para abrir o visualizador de árvore do WPF  
  
1. Em uma DataTip, em uma janela **Inspeção**, **Autos** ou **Locais**, ao lado do nome do objeto do WPF, clique na seta adjacente ao ícone de lupa.  
  
     Uma lista de visualizadores é exibida.  
  
2. Clique em **Visualizador de árvore do WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Para pesquisar a árvore visual  
  
- No painel **Árvore Visual**, digite a cadeia de caracteres que deseja pesquisar na caixa **Pesquisar**.  
  
  O visualizador de árvore do WPF localiza imediatamente o primeiro objeto na árvore visual que corresponde à cadeia de caracteres digitada. Digite mais caracteres para localizar uma correspondência mais precisa.  

  - Para ir para a próxima correspondência na árvore visual, clique em **Avançar**.  

  - Para voltar à correspondência anterior, clique em **Ant**.  

  - Para limpar os critérios de pesquisa, clique em **Limpar**.  

### <a name="to-search-the-properties-list"></a>Para pesquisar a lista de propriedades  
  
- No painel **Propriedades do** _nome_**:**_tipo_ , digite a cadeia de caracteres que deseja pesquisar na caixa de **filtro** .  
  
  O visualizador de árvore do WPF localiza imediatamente as propriedades que correspondem à cadeia de caracteres digitada; agora, a lista exibe apenas as propriedades que correspondem à cadeia de caracteres digitada. Digite mais caracteres para localizar uma correspondência mais precisa.  

  - Para limpar os critérios de pesquisa, clique em **Limpar**.  
  
### <a name="to-close-the-visualizer"></a>Para fechar o visualizador  
  
- Clique no ícone **Fechar** no canto superior direito da caixa de diálogo.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: usar um visualizador](../misc/how-to-use-a-visualizer.md)   
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Árvores no WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Visão geral das propriedades de dependência](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)

---
title: 'Como: usar um visualizador | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778367"
---
# <a name="how-to-use-a-visualizer"></a>Como usar um visualizador
Você pode usar um visualizador para exibir o conteúdo de uma variável ou objeto de uma maneira que seja mais significativa para o tipo de dados. Você pode usar os visualizadores de **DataTips**, uma janela de **inspeção** , a janela **autos** ou a janela **locais** .  
  
 Os visualizadores não têm suporte na Compact Framework.  
  
> [!NOTE]
> Nos aplicativos da **Store** , há suporte apenas para os visualizadores de texto padrão, HTML, XML e JSON. Não há suporte para visualizadores personalizados (criados pelo usuário).  
  
### <a name="to-open-a-visualizer"></a>Para abrir um visualizador  
  
1. Clique no ícone de lupa que aparece ao lado de um nome de variável em **DataTips**, uma janela de **inspeção** ou na janela **automáticos**, **locais**ou de **inspeção rápida** .  
  
     Uma lista de visualizadores é exibida.  
  
2. Clique no visualizador que você deseja usar.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Para usar um visualizador para o código gerenciado durante a depuração remota  
  
- Copie a DLL do visualizador para o computador remoto antes de iniciar a sessão de depuração.  
  
     O caminho para a DLL deve ser o mesmo nos computadores local e remoto. Esse caminho pode ser qualquer um dos seguintes locais:  
  
     *Caminho de instalação do Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     - ou -  
  
     `My Documents\Visual Studio 2010\Visualizers`*Versão do Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>Consulte Também  
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)   
 [Como escrever um visualizador](../debugger/how-to-write-a-visualizer.md)   
 [Exibir valores de dados em dicas de dados](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)
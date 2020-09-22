---
title: 'Como: implementar marcadores de erro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838445"
---
# <a name="how-to-implement-error-markers"></a>Como implementar o marcador de erros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Marcadores de erro (ou sublinhados ondulados em vermelho) são os mais difíceis das personalizações de editor de texto a serem implementadas. No entanto, os benefícios que eles fornecem aos usuários de seu VSPackage podem superar muito o custo para fornecê-los. Marcadores de erro sutimente marcam o texto que seu analisador de idioma considera incorreto com uma linha vermelha ondulada ou vermelho. Esse indicador ajuda os programadores a exibir visualmente o código incorreto.  
  
 Use marcadores de texto para implementar os sublinhados ondulados em vermelho. Como regra, os serviços de linguagem adicionam sublinhados ondulados em vermelho ao buffer de texto como uma passagem em segundo plano, seja em tempo ocioso ou em um thread em segundo plano.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Para implementar o recurso de sublinhado vermelho ondulado  
  
1. Selecione o texto sob o qual você deseja posicionar o sublinhado vermelho ondulado.  
  
2. Crie um marcador do tipo `MARKER_CODESENSE_ERROR` . Para obter mais informações, consulte [como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Depois disso, passe um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ponteiro de interface.  
  
   Esse processo também permite que você crie um texto de dica ou um menu de contexto especial em um determinado marcador. Para obter mais informações, consulte [como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md).  
  
   Os objetos a seguir são necessários antes que os marcadores de erro possam ser exibidos.  
  
- Um analisador.  
  
- Um provedor de tarefas (ou seja, uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> ) que mantém um registro das alterações nas informações de linha para identificar as linhas a serem analisadas novamente.  
  
- Um filtro de exibição de texto que captura eventos de alteração de interpolação do método View using the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> ).  
  
  O analisador, o provedor de tarefas e o filtro fornecem a infraestrutura necessária para tornar os marcadores de erro possíveis. As etapas a seguir fornecem o processo para exibir marcadores de erro.  
  
1. Em uma exibição que está sendo filtrada, o filtro Obtém um ponteiro para o provedor de tarefas associado aos dados dessa exibição.  
  
    > [!NOTE]
    > Você pode usar o mesmo filtro de comando para dicas de método, conclusão de instrução, marcadores de erro e assim por diante.  
  
2. Quando o filtro recebe um evento que indica que você foi movido para outra linha, uma tarefa é criada para verificar se há erros.  
  
3. O manipulador de tarefas verifica se a linha está suja. Nesse caso, ele analisa a linha em busca de erros.  
  
4. Se forem encontrados erros, o provedor de tarefas criará uma instância de item de tarefa. Essa instância cria o marcador de texto que o ambiente usa como um marcador de erro na exibição de texto.  
  
## <a name="see-also"></a>Consulte Também  
 [Usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)   
 [Como criar marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)   
 [Como usar marcadores de texto](../extensibility/how-to-use-text-markers.md)

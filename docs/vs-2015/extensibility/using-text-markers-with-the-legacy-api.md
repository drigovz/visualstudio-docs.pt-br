---
title: Usando marcadores de texto com a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695474"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Usar os marcadores de texto com a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um marcador de texto é um intervalo flutuante de texto em um buffer que pode afetar a exibição e o comportamento de uma região de texto. Os marcadores incluem pontos de interrupção, indicadores, sublinhados ondulados e regiões somente leitura. Os marcadores de texto são basicamente diferentes da cor da sintaxe. A coloração de sintaxe é uma maneira rápida de comunicar a sintaxe da linguagem associada a uma região de texto. A coloração de sintaxe é geralmente solicitada quando o Windows redesenha a tela, quando a velocidade é importante. A coloração de sintaxe altera apenas a cor do texto. Marcadores de texto podem alterar muitas outras propriedades de texto. Os marcadores de texto podem "flutuar" e aplicar o comportamento e a cor especiais.  
  
 Devido à sobrecarga de desempenho associada aos marcadores de texto, não crie muitos marcadores para os buffers de texto. Cada marcador é atualizado toda vez que um usuário edita o conteúdo do buffer.  
  
> [!NOTE]
> Os usuários podem alterar a cor de um tipo de marcador visível, mas não sua forma e estilo. Para obter mais informações, consulte [fontes e cores, ambiente, caixa de diálogo opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como adicionar marcadores de texto padrão](../extensibility/how-to-add-standard-text-markers.md)|Descreve como adicionar um tipo de marcador de texto padrão fornecido pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor de núcleo a uma exibição de texto.|  
|[Como implementar o marcador de erros](../extensibility/how-to-implement-error-markers.md)|Descreve como implementar uma instância do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marcador que é usada para indicar erros usando sublinhados ondulados em vermelho.|  
|[Como criar marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)|Descreve como criar e adicionar um tipo de marcador de texto personalizado a uma exibição de texto.|  
|[Como usar marcadores de texto](../extensibility/how-to-use-text-markers.md)|Explica como adicionar marcadores de texto.|  
|[Dentro do editor principal](../extensibility/inside-the-core-editor.md)|Descreve os recursos do editor principal e fornece detalhes sobre como personalizar o editor de núcleo.|  
|[Recursos do Editor](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Descreve os recursos disponíveis no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal.|  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fornece um mecanismo uniforme para obter informações sobre um tipo de marcador de texto específico, seja predefinido pelo editor ou registrado por um VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Fornece acesso a e ajusta a posição de um marcador de texto em um buffer de texto usando coordenadas bidimensionais.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fornece métodos para gerenciar marcadores de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fornece retornos de chamada para o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE e outros processos que são usados para ajustar um marcador de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Estende a funcionalidade que está disponível por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface fornecendo retornos de chamada adicionais.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Estende a funcionalidade que está disponível por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface fornecendo retornos de chamada adicionais.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Habilita um tipo de marcador para determinar se outros tipos de marcador compartilham o mesmo conjunto de cores.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fornece contexto para marcadores de texto no editor principal. Para cada tipo de marcador de texto que está no editor principal, o IDE cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objeto separado.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Um manipulador que é fornecido para marcadores cujos glifos dão suporte à edição de arrastar e soltar. Um glifo é um ícone que indica a posição de um marcador.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Retorna uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interface de um serviço que fornece marcadores de texto para outros VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Fornece acesso a e ajusta a posição de um marcador de texto em um buffer de texto usando coordenadas unidimensionais. Se possível, não use essa interface.

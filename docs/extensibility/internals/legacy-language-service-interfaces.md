---
title: Interfaces de serviço de idioma legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707383"
---
# <a name="legacy-language-service-interfaces"></a>Interfaces de serviço de linguagem herdada
Para qualquer linguagem de programação específica, pode haver apenas uma instância de um serviço de idiomas por vez. No entanto, um único serviço de idiomas pode servir mais de um editor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]não associa um serviço de idioma saque a nenhum editor em particular. Portanto, quando você solicita uma operação de serviço de idioma, você deve identificar o editor apropriado como um parâmetro.

## <a name="common-interfaces-associated-with-language-services"></a>Interfaces comuns associadas aos serviços de idioma
 O editor obtém seu <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> serviço de idioma saqueando o VSPackage apropriado. O ID de serviço (SID) aprovado nesta chamada identifica o serviço de idioma saudoso que está sendo solicitado.

 Você pode implementar as interfaces de serviço de idioma principal em qualquer número de classes separadas. No entanto, uma abordagem comum é implementar as seguintes interfaces em uma única classe:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (opcional)

  A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface deve ser implementada em todos os serviços de idiomas. Ele fornece informações sobre o seu serviço de idioma, como o nome localizado do idioma, as extensões de nome do arquivo associadas ao serviço de idioma e como recuperar um colorador.

## <a name="additional-language-service-interfaces"></a>Interfaces adicionais de serviço de idioma
 Outras interfaces podem ser fornecidas com o seu serviço de idioma. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]solicita uma instância separada dessas interfaces para cada instância do buffer de texto. Portanto, você deve implementar cada uma dessas interfaces em seu próprio objeto. A tabela a seguir mostra interfaces que requerem uma instância por instância de buffer de texto.

|Interface|Descrição|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gerencia adornos de janela de código, como a barra de saque. Você pode obter esta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> interface usando o método. Há uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> por janela de código.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore palavras-chave e delimitadores de linguagem. Você pode obter esta <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> interface usando o método. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>é chamado na hora da pintura. Evite o trabalho intensivo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> de computação dentro ou o desempenho pode sofrer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornece dicas de ferramentas de parâmetros do IntelliSense. Quando o serviço de idioma reconhece um caractere que indica que os dados do método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> devem ser exibidos, como um parêntese aberto, ele chama o método para notificar a exibição de texto de que o serviço de idioma está pronto para exibir uma Dica de Ferramenta de Informações do Parâmetro. Em seguida, a visualização de texto chama de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> volta para o serviço de idiomausando os métodos da interface para obter as informações necessárias para exibir a dica de ferramenta.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Fornece a conclusão da declaração do IntelliSense. Quando o serviço de idioma está pronto para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> exibir uma lista de conclusão, ele chama o método na exibição de texto. Em seguida, a visualização de texto chama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> de volta para o serviço de idioma usando métodos no objeto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Permite a modificação da exibição de texto usando o manipulador de comando. A classe em que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> você implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a interface também deve implementar a interface. A exibição de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> texto recupera o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objeto consultando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> o objeto que é passado para o método. Deve haver <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> um objeto para cada visão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Intercepta comandos que o usuário digita na janela de código. Monitore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> saída de sua implementação para fornecer informações de conclusão personalizadas e visualizar a modificação<br /><br /> Para passar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> seu objeto para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>a exibição de texto, ligue .|

## <a name="see-also"></a>Confira também
- [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Lista de verificação: criando um serviço de linguagem herdado](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

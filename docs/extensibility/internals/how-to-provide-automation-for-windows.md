---
title: 'Como: Fornecer automação para Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707957"
---
# <a name="how-to-provide-automation-for-windows"></a>Como: Fornecer automação para windows

Você pode fornecer automação para janelas de documentos e ferramentas. Fornecer automação é aconselhável sempre que você quiser disponibilizar objetos de automação em uma janela, e o ambiente ainda não fornece um objeto de automação pronto, como faz com uma lista de tarefas.

## <a name="automation-for-tool-windows"></a>Automação para janelas de ferramentas

O ambiente fornece automação em uma janela <xref:EnvDTE.Window> de ferramenta retornando um objeto padrão, conforme explicado no procedimento a seguir:

1. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> para o método através do ambiente com [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` como parâmetro para `Window` pegar o objeto.

2. Quando um chamador solicita um objeto de automação <xref:EnvDTE.Window.Object%2A>específico do `QueryInterface` `IExtensibleObject`VSPackage para a janela da ferramenta através, o ambiente exige <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou as `IDispatch` interfaces. Ambos `IExtensibleObject` `IVsExtensibleObject` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> fornecer um método.

3. Quando o ambiente `GetAutomationObject` então `NULL`chamar o método de passagem, responda repassando seu objeto específico do VSPackage.

4. Se `QueryInterface` o `IExtensibleObject` `IVsExtensibleObject` chamado e falhar, `QueryInterface` `IDispatch`então o ambiente exige .

## <a name="automation-for-document-windows"></a>Automação para janelas de documentos

Um <xref:EnvDTE.Document> objeto padrão também está disponível no ambiente, embora <xref:EnvDTE.Document> um editor `IExtensibleObject` possa ter `GetAutomationObject`sua própria implementação do objeto implementando interface e respondendo a .

Além disso, um editor pode fornecer um objeto de <xref:EnvDTE.Document.Object%2A> automação específico do `IVsExtensibleObject` VSPackage, recuperado através do método, implementando as interfaces ou. `IExtensibleObject` As [amostras VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuem com um objeto de automação específico de documento RTF.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

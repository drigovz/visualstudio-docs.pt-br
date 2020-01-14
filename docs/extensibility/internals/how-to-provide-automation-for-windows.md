---
title: 'Como: fornecer automação para o Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848849"
---
# <a name="how-to-provide-automation-for-windows"></a>Como: fornecer automação para o Windows

Você pode fornecer automação para janelas de documentos e ferramentas. Fornecer automação é aconselhável sempre que você deseja disponibilizar objetos de automação em uma janela, e o ambiente ainda não fornece um objeto de automação pronto, como faz com uma lista de tarefas.

## <a name="automation-for-tool-windows"></a>Automação para janelas de ferramentas

O ambiente fornece automação em uma janela de ferramenta retornando um objeto de <xref:EnvDTE.Window> padrão, conforme explicado no procedimento a seguir:

1. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> por meio do ambiente com [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) como `VSFPROPID` parâmetro para obter o objeto `Window`.

2. Quando um chamador solicita um objeto de automação específico do VSPackage para sua janela de ferramentas por meio de <xref:EnvDTE.Window.Object%2A>, o ambiente chama `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>ou as interfaces `IDispatch`. Tanto `IExtensibleObject` quanto `IVsExtensibleObject` fornecem um método <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Quando o ambiente chama o método `GetAutomationObject` passando `NULL`, responda passando o objeto específico do VSPackage.

4. Se a chamada de `QueryInterface` para `IExtensibleObject` e `IVsExtensibleObject` falhar, o ambiente chamará `QueryInterface` para `IDispatch`.

## <a name="automation-for-document-windows"></a>Automação para janelas de documentos

Um objeto de <xref:EnvDTE.Document> padrão também está disponível no ambiente, embora um editor possa ter sua própria implementação do objeto <xref:EnvDTE.Document> implementando a interface `IExtensibleObject` e respondendo a `GetAutomationObject`.

Além disso, um editor pode fornecer um objeto de automação específico do VSPackage, recuperado por meio do método <xref:EnvDTE.Document.Object%2A>, implementando as interfaces `IVsExtensibleObject` ou `IExtensibleObject`. Os [exemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) contribuem com um objeto de automação de RTF específico do documento.

## <a name="see-also"></a>Veja também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

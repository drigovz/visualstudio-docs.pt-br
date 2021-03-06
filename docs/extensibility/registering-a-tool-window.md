---
title: Registrando uma janela de ferramentas | Microsoft Docs
description: Saiba como você pode registrar suas janelas de ferramentas com o Visual Studio usando ProvideToolWindowAttribute e ProvideToolWindowVisibilityAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79f830d0a035dbea503ffbbc05ae30acfeb16766
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837028"
---
# <a name="register-a-tool-window"></a>Registrar uma janela de ferramentas
Você pode registrar suas janelas de ferramentas usando o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e o  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Exemplo

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 No código acima, o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registra as `PersistedWindowPane` janelas de `DynamicWindowPane` ferramentas e com o Visual Studio. A janela de ferramentas persistentes é encaixada e tabulada com **Gerenciador de soluções**, e a janela dinâmica recebe uma posição inicial e um tamanho padrão. A janela dinâmica torna-se transitória, o que indica que ela não é criada na inicialização. Isso grava um `DontForceCreate` valor na `ToolWindows` chave no registro do sistema. Para obter mais informações, consulte [configuração de exibição da janela de ferramentas](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015).
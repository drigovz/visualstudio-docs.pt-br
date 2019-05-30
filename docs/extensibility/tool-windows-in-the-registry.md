---
title: Ferramenta do Windows no registro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b74081f474e85b97f46db5250daf042dbd6b917
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316389"
---
# <a name="tool-windows-in-the-registry"></a>Janela de ferramentas no registro
Os VSPackages que fornecem as janelas de ferramentas deve registrar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como provedores de janela de ferramentas. Janelas de ferramentas criadas usando o modelo de pacote do Visual Studio fazer isso por padrão. Provedores de janela de ferramenta têm chaves de registro do sistema que especifica os atributos de visibilidade, como tamanho de janela de ferramenta padrão e o local, o GUID da janela que serve como o painel de janela de ferramentas e o estilo de encaixe.

 Durante o desenvolvimento, provedores de janela de ferramenta gerenciado registrar janelas de ferramentas adicionando atributos no código-fonte, e em seguida, executando o utilitário RegPkg.exe o assembly resultante. Para obter mais informações, consulte [registrando uma janela de ferramentas](../extensibility/registering-a-tool-window.md).

## <a name="registering-unmanaged-tool-window-providers"></a>Registrando provedores de janela de ferramenta não gerenciado
 Provedores de janela de ferramenta não gerenciado devem registrar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na seção Windows 2000ferramenta de registro do sistema. O fragmento de arquivo. reg a seguir mostra como uma janela de ferramenta dinâmica pode ser registrada:

```
- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"
"Float"="250, 250, 410, 430"
"DontForceCreate"=dword:00000001

- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000
```

 Na primeira chave no exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tais como 7.1 ou 8.0, a subchave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} é o GUID do painel de janela de ferramentas (DynamicWindowPane) e o {de valor padrão 01069cdd-95ce-4620-Ac21-ddff6c57f012} é o GUID do VSPackage fornecendo a janela da ferramenta. Para obter uma explicação das subchaves Float e DontForceCreate, consulte [configuração de exibição da janela de ferramenta](../extensibility/tool-window-display-configuration.md).

 A segunda chave opcional ToolWindows\Visibility, especifica os GUIDs dos comandos que exigem a janela da ferramenta para ficar visível. Nesse caso, não há nenhum comando especificado. Para obter mais informações, consulte [configuração de exibição da janela de ferramenta](../extensibility/tool-window-display-configuration.md).

## <a name="see-also"></a>Consulte também
- [VSPackages](../extensibility/internals/vspackages.md)
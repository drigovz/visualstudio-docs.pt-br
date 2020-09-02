---
title: Janelas de ferramentas no registro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186380"
---
# <a name="tool-windows-in-the-registry"></a>Janela de ferramentas no registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages que fornecem janelas de ferramentas devem se registrar no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] como provedores de janelas de ferramentas. As janelas de ferramentas criadas usando o modelo de pacote do Visual Studio fazem isso por padrão. Os provedores de janela de ferramentas têm chaves do registro do sistema que especificam atributos de visibilidade, como o tamanho e o local da janela de ferramentas padrão, o GUID da janela que serve como o painel da janela de ferramentas e o estilo de encaixe.  
  
 Durante o desenvolvimento, os provedores de janelas de ferramentas gerenciadas registram as janelas de ferramentas adicionando atributos ao código-fonte e, em seguida, executando o utilitário de RegPkg.exe no assembly resultante. Para obter mais informações, consulte [registrando uma janela de ferramentas](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrando provedores de janela de ferramentas não gerenciadas  
 Os provedores de janela de ferramentas não gerenciados devem se registrar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no na seção ToolWindows do registro do sistema. O fragmento de arquivo. reg a seguir mostra como uma janela de ferramenta dinâmica pode ser registrada:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Na primeira chave no exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , como 7,1 ou 8,0, a subchave {f0e1e9a1-9860-484d-ad5d-367d79aabf55} é o GUID do painel da janela de ferramentas (DynamicWindowPane) e o valor padrão {01069cdd-95ce-4620-Ac21-ddff6c57f012} é o GUID do VSPackage que fornece a janela de ferramentas. Para obter uma explicação das subchaves float e DontForceCreate, consulte [configuração de exibição da janela de ferramentas](../extensibility/tool-window-display-configuration.md).  
  
 A segunda chave opcional, ToolWindows\Visibility, especifica os GUIDs de comandos que exigem que a janela de ferramentas fique visível. Nesse caso, não há nenhum comando especificado. Para obter mais informações, consulte [configuração de exibição da janela de ferramentas](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Conceitos básicos do VSPackage](../misc/vspackage-essentials.md)

---
title: '&lt;&gt;elemento TrustInfo (aplicativo ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca7e19925288b1509fec08235f546b84b4afffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62420064"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;&gt;elemento TrustInfo (aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descreve as permissões de segurança mínimas necessárias para que o aplicativo seja executado no computador cliente.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `trustInfo` elemento é obrigatório e está no `asm.v2` namespace. Ele não tem atributos e contém os elementos a seguir.  
  
## <a name="security"></a>segurança  
 Obrigatórios. Esse elemento é um filho do `trustInfo` elemento. Ele contém o `applicationRequestMinimum` elemento e não tem nenhum atributo.  
  
## <a name="applicationrequestminimum"></a>applicationRequestMinimum  
 Obrigatórios. Esse elemento é um filho do `security` elemento e contém os `PermissionSet` elementos, e `assemblyRequest` `defaultAssemblyRequest` . Esse elemento não tem atributos.  
  
## <a name="permissionset"></a>PermissionSet  
 Obrigatórios. Esse elemento é um filho do `applicationRequestMinimum` elemento e contém o `IPermission` elemento. Esse elemento tem os atributos a seguir.  
  
- `ID`  
  
     Obrigatórios. Identifica o conjunto de permissões. Esse atributo pode ser qualquer valor. A ID é referenciada nos `defaultAssemblyRequest` `assemblyRequest` atributos e.  
  
- `version`  
  
     Obrigatórios. Identifica a versão da permissão. Normalmente, esse valor é `1` .  
  
## <a name="ipermission"></a>IPermission  
 Opcional. Esse elemento é um filho do `PermissionSet` elemento. O `IPermission` elemento identifica totalmente uma classe de permissão no [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . O `IPermission` elemento tem os atributos a seguir, mas pode ter atributos adicionais que correspondam às propriedades na classe de permissão. Para descobrir a sintaxe de uma permissão específica, consulte os exemplos listados no arquivo de Security.config.  
  
- `class`  
  
     Obrigatórios. Identifica a classe de permissão por nome forte. Por exemplo, o código a seguir identifica o `FileDialogPermission` tipo.  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
- `version`  
  
     Obrigatórios. Identifica a versão da permissão. Normalmente, esse valor é `1` .  
  
- `Unrestricted`  
  
     Obrigatórios. Identifica se o aplicativo precisa de uma concessão irrestrita dessa permissão. Se `true` , a concessão de permissão é incondicional. Se `false` , ou se esse atributo for indefinido, ele será restrito de acordo com os atributos específicos de permissão definidos na `IPermission` marca. Adote as seguintes permissões:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     Neste exemplo, a declaração para <xref:System.Security.Permissions.EnvironmentPermission> restringe o aplicativo a ler apenas a variável de ambiente username, enquanto a declaração para <xref:System.Security.Permissions.FileDialogPermission> fornece ao aplicativo o uso irrestrito de todas as <xref:System.Windows.Forms.FileDialog> classes.  
  
## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest  
 Opcional. Identifica o conjunto de permissões concedidas a todos os assemblies. Esse elemento é um filho do `applicationRequestMinimum` elemento e tem o atributo a seguir.  
  
- `permissionSetReference`  
  
     Obrigatórios. Identifica a ID do conjunto de permissões que é a permissão padrão. O conjunto de permissões é declarado no `PermissionSet` elemento.  
  
## <a name="assemblyrequest"></a>assemblyRequest  
 Opcional. Identifica as permissões para um assembly específico. Esse elemento é um filho do `applicationRequestMinimum` elemento e tem os atributos a seguir.  
  
- `Name`  
  
     Obrigatórios. Identifica o nome do assembly.  
  
- `permissionSetReference`  
  
     Obrigatórios. Identifica a ID do conjunto de permissões que este assembly requer. O conjunto de permissões é declarado no `PermissionSet` elemento.  
  
## <a name="requestedprivileges"></a>requestedPrivileges  
 Opcional. Esse elemento é um filho do `security` elemento e contém o `requestedExecutionLevel` elemento. Esse elemento não tem atributos.  
  
## <a name="requestedexecutionlevel"></a>requestedExecutionLevel  
 Opcional. Identifica o nível de segurança no qual o aplicativo solicita a execução. Este elemento não tem filhos e tem os atributos a seguir.  
  
- `Level`  
  
     Obrigatórios. Indica o nível de segurança que o aplicativo está solicitando. Os valores possíveis são:  
  
     `asInvoker`, não solicitando permissões adicionais. Esse nível não requer prompts de confiança adicionais.  
  
     `highestAvailable`, solicitando as permissões mais altas disponíveis para o processo pai.  
  
     `requireAdministrator`, solicitando permissões de administrador completo.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos serão instalados apenas com um valor de `asInvoker` . A instalação com qualquer outro valor falhará.  
  
- `uiAccess`  
  
     Opcional. Indica se o aplicativo requer acesso a elementos protegidos da interface do usuário. Os valores são `true` ou `false` , e o padrão é false. Somente aplicativos assinados devem ter um valor de true.  
  
## <a name="remarks"></a>Comentários  
 Se um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo solicitar mais permissões do que o computador cliente concederá por padrão, o Gerenciador de confiança do Common Language Runtime perguntará ao usuário se ele deseja conceder ao aplicativo esse nível elevado de confiança. Se ela disser não, o aplicativo não será executado; caso contrário, ele será executado com as permissões solicitadas.  
  
 Todas as permissões solicitadas usando `defaultAssemblyRequest` e `assemblyRequest` serão concedidas sem que o usuário solicite se o manifesto de implantação tiver uma licença de confiança válida.  
  
 Para obter mais informações sobre elevação de permissões, consulte [Securing ClickOnce Applications](../deployment/securing-clickonce-applications.md). Para obter mais informações sobre a implantação de política, consulte [visão geral da implantação de aplicativo confiável](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="examples"></a>Exemplos  
 Os três exemplos de código a seguir ilustram `trustInfo` elementos para as zonas de segurança padrão nomeadas — Internet, LocalIntranet e FullTrust — para uso no [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto do aplicativo de uma implantação.  
  
 O primeiro exemplo ilustra o `trustInfo` elemento para as permissões padrão disponíveis na zona de segurança da Internet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 O segundo exemplo ilustra o `trustInfo` elemento para as permissões padrão disponíveis na zona de segurança LocalIntranet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 O terceiro exemplo ilustra o `trustInfo` elemento para as permissões padrão disponíveis na zona de segurança FullTrust.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)

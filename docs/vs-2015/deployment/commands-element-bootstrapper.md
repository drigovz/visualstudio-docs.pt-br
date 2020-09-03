---
title: '&lt;Elemento Commands &gt; (Bootstrapper) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af10c9e0b26a6ef2c8e7a98bc345b8e86017682b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205343"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Elemento Commands &gt; (Bootstrapper)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O `Commands` elemento implementa testes descritos pelos elementos abaixo do `InstallChecks` elemento e declara qual pacote o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bootstrapper deve instalar se o teste falhar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `Commands` elemento é obrigatório. O elemento tem o atributo a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Reboot`|Opcional. Determina se o sistema deve ser reiniciado se algum dos pacotes retornar um código de saída de reinicialização. A lista a seguir mostra os valores válidos:<br /><br /> `Defer`. A reinicialização é adiada até algum momento futuro.<br /><br /> `Immediate`. Causará uma reinicialização imediata se um dos pacotes retornar um código de saída de reinicialização.<br /><br /> `None`. Faz com que todas as solicitações de reinicialização sejam ignoradas.<br /><br /> O padrão é `Immediate`.|  
  
## <a name="command"></a>Comando  
 O `Command` é um elemento filho do elemento `Commands`. Um `Commands` elemento pode ter um ou mais `Command` elementos. O elemento tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`PackageFile`|Obrigatórios. O nome do pacote a ser instalado deve ter uma ou mais das condições especificadas por `InstallConditions` retornar false. O pacote deve ser definido no mesmo arquivo usando um `PackageFile` elemento.|  
|`Arguments`|Opcional. Um conjunto de argumentos de linha de comando para passar para o arquivo de pacote.|  
|`EstimatedInstallSeconds`|Opcional. O tempo estimado, em segundos, que será necessário para instalar o pacote. Esse valor determina o tamanho da barra de progresso que o bootstrapper exibe para o usuário. O padrão é 0, caso em que nenhuma estimativa de tempo é especificada.|  
|`EstimatedDiskBytes`|Opcional. A quantidade estimada de espaço em disco, em bytes, que o pacote ocupará depois que a instalação for concluída. Esse valor é usado em requisitos de espaço em disco rígido que o bootstrapper exibe para o usuário. O padrão é 0; nesse caso, o bootstrapper não exibe requisitos de espaço em disco rígido.|  
|`EstimatedTempBytes`|Opcional. A quantidade estimada de espaço em disco temporário, em bytes, que será necessária para o pacote.|  
|`Log`|Opcional. O caminho para o arquivo de log que o pacote gera, em relação ao diretório raiz do pacote.|  
  
## <a name="installconditions"></a>InstallConditions  
 O `InstallConditions` elemento é um filho do `Command` elemento. Cada `Command` elemento pode ter no máximo um `InstallConditions` elemento. Se nenhum `InstallConditions` elemento existir, o pacote especificado pelo `Condition` sempre será executado.  
  
## <a name="bypassif"></a>BypassIf  
 O `BypassIf` elemento é um filho do `InstallConditions` elemento e descreve uma condição positiva sob a qual o comando não deve ser executado. Cada `InstallConditions` elemento pode ter zero ou mais `BypassIf` elementos.  
  
 `BypassIf` tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Obrigatórios. O nome da propriedade a ser testada. A propriedade deve ter sido definida anteriormente por um filho do `InstallChecks` elemento. Para obter mais informações, consulte [ \<InstallChecks> elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obrigatórios. O tipo de comparação a ser executada. A lista a seguir mostra os valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obrigatórios. O valor a ser comparado com a propriedade.|  
|`Schedule`|Opcional. O nome de uma `Schedule` marca que define quando essa regra deve ser avaliada.|  
  
## <a name="failif"></a>FailIf  
 O `FailIf` elemento é um filho do `InstallConditions` elemento e descreve uma condição positiva sob a qual a instalação deve parar. Cada `InstallConditions` elemento pode ter zero ou mais `FailIf` elementos.  
  
 `FailIf` tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Property`|Obrigatórios. O nome da propriedade a ser testada. A propriedade deve ter sido definida anteriormente por um filho do `InstallChecks` elemento. Para obter mais informações, consulte [ \<InstallChecks> elemento](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obrigatórios. O tipo de comparação a ser executada. A lista a seguir mostra os valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obrigatórios. O valor a ser comparado com a propriedade.|  
|`String`|Opcional. O texto a ser exibido para o usuário após a falha.|  
|`Schedule`|Opcional. O nome de uma `Schedule` marca que define quando essa regra deve ser avaliada.|  
  
## <a name="exitcodes"></a> ExitCodes  
 O `ExitCodes` elemento é um filho do `Command` elemento. O `ExitCodes` elemento contém um ou mais `ExitCode` elementos, que determinam o que a instalação deve fazer em resposta a um código de saída de um pacote. Pode haver um elemento opcional `ExitCode` abaixo de um `Command` elemento. `ExitCodes` não tem atributos.  
  
## <a name="exitcode"></a>ExitCode  
 O `ExitCode` elemento é um filho do `ExitCodes` elemento. O `ExitCode` elemento determina o que a instalação deve fazer em resposta a um código de saída de um pacote. `ExitCode` Não contém nenhum elemento filho e tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Value`|Obrigatórios. O valor do código de saída ao qual esse `ExitCode` elemento se aplica.|  
|`Result`|Obrigatórios. Como a instalação deve reagir a esse código de saída. A lista a seguir mostra os valores válidos:<br /><br /> `Success`. Sinaliza o pacote como instalado com êxito.<br /><br /> `SuccessReboot`. Sinaliza o pacote como instalado com êxito e instrui o sistema a reiniciar.<br /><br /> `Fail`. Sinaliza o pacote como com falha.<br /><br /> `FailReboot`. Sinaliza o pacote como com falha e instrui o sistema a reiniciar.|  
|`String`|Opcional. O valor a ser exibido para o usuário em resposta a este código de saída.|  
|`FormatMessageFromSystem`|Opcional. Determina se deve ser usada a mensagem de erro fornecida pelo sistema correspondente ao código de saída ou usar o valor fornecido em `String` . Os valores válidos são `true` , o que significa usar o erro fornecido pelo sistema e `false` , que significa usar a cadeia de caracteres fornecida pelo `String` . O padrão é `false`. Se essa propriedade for `false` , mas `String` não estiver definida, o erro fornecido pelo sistema será usado.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir define os comandos para instalar o .NET Framework 2,0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks> Elementos](../deployment/installchecks-element-bootstrapper.md)

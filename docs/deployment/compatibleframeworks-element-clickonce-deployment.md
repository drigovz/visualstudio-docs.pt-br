---
title: '&lt;compatibleFrameworks&gt; elemento (implantação do ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99db3d51414197df469aaa2eabe97e0967c31b05
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746039"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elemento (implantação do ClickOnce)
Identifica as versões do .NET Framework em que este aplicativo pode instalar e executar.

> [!NOTE]
> [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) não oferece suporte a `compatibleFrameworks` elemento ao salvar um manifesto de aplicativo que já foi assinado com um certificado usando [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Em vez disso, você deve usar [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Sintaxe

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `compatibleFrameworks` elemento é necessário para manifestos de implantação que se destinam a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tempo de execução fornecido pelo .NET Framework 4 ou posterior. O `compatibleFrameworks` elemento contém um ou mais `framework` elementos que especificam as versões do .NET Framework em que esse aplicativo pode ser executado. O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tempo de execução executará o aplicativo na primeira disponível `framework` nessa lista.

 A tabela a seguir lista o atributo que o `compatibleFrameworks` dá suporte ao elemento.

|Atributo|Descrição|
|---------------|-----------------|
|`S` `upportUrl`|Opcional. Especifica uma URL em que a versão do .NET Framework compatível preferida pode ser baixada.|

## <a name="framework"></a>estrutura
 Necessário. A tabela a seguir lista os atributos que o `framework` dá suporte ao elemento.

|Atributo|Descrição|
|---------------|-----------------|
|`targetVersion`|Necessário. Especifica o número de versão do .NET Framework de destino.|
|`profile`|Necessário. Especifica o perfil de destino do .NET Framework.|
|`supportedRuntime`|Necessário. Especifica o número de versão do tempo de execução associado com o .NET Framework de destino.|

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 O seguinte exemplo de código mostra uma `compatibleFrameworks` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de implantação. Essa implantação pode ser executado no [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Ele também pode executar no .NET Framework 4 porque ele é um superconjunto do [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Consulte também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
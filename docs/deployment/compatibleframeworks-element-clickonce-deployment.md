---
title: '&lt;&gt;elemento CompatibleFrameworks (implantação do ClickOnce) | Microsoft Docs'
description: O elemento compatibleFrameworks identifica as versões do .NET Framework em que esse aplicativo pode ser instalado e executado.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b0a87e36a176a01b8f243c4646e2711220f807f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881172"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;elemento CompatibleFrameworks (implantação do ClickOnce)
Identifica as versões do .NET Framework em que esse aplicativo pode ser instalado e executado.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) não oferece suporte ao `compatibleFrameworks` elemento ao salvar um manifesto de aplicativo que já tenha sido assinado com um certificado usando [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Em vez disso, você deve usar [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

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
 O `compatibleFrameworks` elemento é necessário para os manifestos de implantação destinados ao [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tempo de execução fornecido pelo .NET Framework 4 ou posterior. O `compatibleFrameworks` elemento contém um ou mais `framework` elementos que especificam as versões de .NET Framework nas quais esse aplicativo pode ser executado. O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tempo de execução executará o aplicativo no primeiro disponível `framework` nesta lista.

 A tabela a seguir lista o atributo ao qual o `compatibleFrameworks` elemento dá suporte.

|Atributo|Descrição|
|---------------|-----------------|
|`S` `upportUrl`|Opcional. Especifica uma URL em que a versão de .NET Framework compatível preferencial pode ser baixada.|

## <a name="framework"></a>estrutura
 Obrigatório. A tabela a seguir lista os atributos aos quais o `framework` elemento dá suporte.

|Atributo|Descrição|
|---------------|-----------------|
|`targetVersion`|Obrigatórios. Especifica o número de versão do .NET Framework de destino.|
|`profile`|Obrigatório. Especifica o perfil do .NET Framework de destino.|
|`supportedRuntime`|Obrigatório. Especifica o número de versão do tempo de execução associado ao .NET Framework de destino.|

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 O exemplo de código a seguir mostra um `compatibleFrameworks` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de implantação. Essa implantação pode ser executada no [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Ele também pode ser executado no .NET Framework 4 porque ele é um superconjunto do [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
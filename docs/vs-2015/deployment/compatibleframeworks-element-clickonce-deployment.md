---
title: '&lt;&gt;elemento CompatibleFrameworks (implantação do ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675422"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;elemento CompatibleFrameworks (implantação do ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica as versões do .NET Framework em que esse aplicativo pode ser instalado e executado.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) não oferece suporte ao `compatibleFrameworks` elemento ao salvar um manifesto de aplicativo que já tenha sido assinado com um certificado usando [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Em vez disso, você deve usar [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 O `compatibleFrameworks` elemento é necessário para os manifestos de implantação destinados ao [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tempo de execução fornecido pelo [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou posterior. O `compatibleFrameworks` elemento contém um ou mais `framework` elementos que especificam as versões de .NET Framework nas quais esse aplicativo pode ser executado. O [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tempo de execução executará o aplicativo no primeiro disponível `framework` nesta lista.  
  
 A tabela a seguir lista o atributo ao qual o `compatibleFrameworks` elemento dá suporte.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`S` `upportUrl`|Opcional. Especifica uma URL em que a versão de .NET Framework compatível preferencial pode ser baixada.|  
  
## <a name="framework"></a>estrutura  
 Obrigatórios. A tabela a seguir lista os atributos aos quais o `framework` elemento dá suporte.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`targetVersion`|Obrigatórios. Especifica o número de versão do .NET Framework de destino.|  
|`profile`|Obrigatórios. Especifica o perfil do .NET Framework de destino.|  
|`supportedRuntime`|Obrigatórios. Especifica o número de versão do tempo de execução associado ao .NET Framework de destino.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra um `compatibleFrameworks` elemento em um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto de implantação. Essa implantação pode ser executada no [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Ele também pode ser executado no [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] porque é um superconjunto do [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)

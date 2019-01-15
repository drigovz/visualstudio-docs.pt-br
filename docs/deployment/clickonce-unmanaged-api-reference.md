---
title: Referência da API não gerenciada do ClickOnce | Microsoft Docs
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 584dc441e54e89fea77667cac98cdad78bac5b2d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968128"
---
# <a name="clickonce-unmanaged-api-reference"></a>Referência de API não gerenciada do ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] APIs públicas não gerenciadas de dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Limpa ou desinstala todos os aplicativos de online o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache do aplicativo.  
  
### <a name="return-value"></a>Valor retornado  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um HRESULT que representa a falha. Se ocorrer uma exceção gerenciada, retorna 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Comentários  
 Chamar CleanOnlineAppCache iniciará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do serviço se ainda não estiver sendo executado.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Recupera informações sobre a implantação da URL de manifesto e a ativação.  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Um ponteiro para o `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Um ponteiro para o `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Um ponteiro para um buffer para recebimento de uma cadeia de caracteres terminada em nulo que especifica a identidade do aplicativo completo é retornado.|LPWSTR|  
|`pdwIdentityBufferLength`|Um ponteiro para um DWORD que é o comprimento de `pwzApplicationIdentity` buffer, em WCHARs. Isso inclui o espaço para o caractere nulo de terminação.|LPDWORD|  
|`pwzProcessorArchitecture`|Um ponteiro para um buffer para recebimento de uma cadeia de caracteres terminada em nulo que especifica a arquitetura do processador da implantação do aplicativo do manifesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Um ponteiro para um DWORD que é o comprimento de `pwzProcessorArchitecture` buffer, em WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Um ponteiro para um buffer para recebimento de uma cadeia de caracteres terminada em nulo que especifica a base de código do manifesto do aplicativo do manifesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Um ponteiro para um DWORD que é o comprimento de `pwzApplicationManifestCodebase` buffer, em WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Um ponteiro para um buffer para recebimento de uma cadeia de caracteres terminada em nulo que especifica o provedor de implantação do manifesto, se estiver presente. Caso contrário, uma cadeia de caracteres vazia é retornada.|LPWSTR|  
|`pdwProviderBufferLength`|Um ponteiro para um DWORD que é o comprimento de `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valor retornado  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um HRESULT que representa a falha. Retorna HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER) se um buffer for muito pequeno.  
  
### <a name="remarks"></a>Comentários  
 Ponteiros não devem ser nulos. `pcwzActivationUrl` e `pcwzPathToDeploymentManifest` não pode estar vazio.  
  
 É responsabilidade do chamador para limpar a URL de ativação. Por exemplo, a adição de escape caracteres onde eles são necessários ou removendo a cadeia de caracteres de consulta.  
  
 É responsabilidade do chamador para limitar o tamanho de entrada. Por exemplo, o tamanho máximo da URL é 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Inicia ou instala um aplicativo usando uma URL de implantação.  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|Tipo|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Um ponteiro para uma cadeia de caracteres terminada em nulo que contém a URL do manifesto de implantação.|LPCWSTR|  
|`data`|Reservado para uso futuro. Precisa ser NULL.|LPVOID|  
|`flags`|Reservado para uso futuro. Precisa ser 0.|DWORD|  
  
### <a name="return-value"></a>Valor retornado  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um HRESULT que representa a falha. Se ocorrer uma exceção gerenciada, retorna 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>
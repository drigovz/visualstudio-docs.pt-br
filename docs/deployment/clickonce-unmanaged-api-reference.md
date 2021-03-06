---
title: Referência de API não gerenciada do ClickOnce | Microsoft Docs
description: Saiba mais sobre as APIs públicas não gerenciadas do ClickOnce de dfshim.dll, incluindo CleanOnlineAppCache, GetDeploymentDataFromManifest e LaunchApplication.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 88d8147dded05c6bec54682e76c6a8c1826b43e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900803"
---
# <a name="clickonce-unmanaged-api-reference"></a>Referência de API não gerenciada do ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] APIs públicas não gerenciadas do dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Limpa ou desinstala todos os aplicativos online do cache de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos.

### <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um HRESULT que representa a falha. Se ocorrer uma exceção gerenciada, retornará 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Comentários
 Chamar CleanOnlineAppCache iniciará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] serviço se ele ainda não estiver em execução.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Recupera informações de implantação do manifesto e da URL de ativação.

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|Type|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Um ponteiro para o `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Um ponteiro para o `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica a identidade de aplicativo completa retornada.|LPWSTR|
|`pdwIdentityBufferLength`|Um ponteiro para um DWORD que é o comprimento do `pwzApplicationIdentity` buffer, em WCHARs. Isso inclui o espaço para o caractere de terminação NULL.|LPDWORD|
|`pwzProcessorArchitecture`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica a arquitetura do processador da implantação do aplicativo, do manifesto.|LPWSTR|
|`pdwArchitectureBufferLength`|Um ponteiro para um DWORD que é o comprimento do `pwzProcessorArchitecture` buffer, em WCHARs.|LPDWORD|
|`pwzApplicationManifestCodebase`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica a codebase do manifesto do aplicativo, do manifesto.|LPWSTR|
|`pdwCodebaseBufferLength`|Um ponteiro para um DWORD que é o comprimento do `pwzApplicationManifestCodebase` buffer, em WCHARs.|LPDWORD|
|`pwzDeploymentProvider`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica o provedor de implantação do manifesto, se presente. Caso contrário, uma cadeia de caracteres vazia será retornada.|LPWSTR|
|`pdwProviderBufferLength`|Um ponteiro para um DWORD que é o comprimento do `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um HRESULT que representa a falha. Retorna HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) se um buffer for muito pequeno.

### <a name="remarks"></a>Comentários
 Os ponteiros não devem ser nulos. `pcwzActivationUrl` e `pcwzPathToDeploymentManifest` não deve ficar vazio.

 É responsabilidade do chamador limpar a URL de ativação. Por exemplo, adicionar caracteres de escape onde eles são necessários ou remover a cadeia de caracteres de consulta.

 É responsabilidade do chamador limitar o comprimento de entrada. Por exemplo, o comprimento máximo da URL é 2 KB.

## <a name="launchapplication"></a>LaunchApplication
 Inicia ou instala um aplicativo usando uma URL de implantação.

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|Type|
|---------------|-----------------|----------|
|`deploymentUrl`|Um ponteiro para uma cadeia de caracteres terminada em nulo que contém a URL do manifesto de implantação.|LPCWSTR|
|`data`|Reservado para uso futuro. Precisa ser NULL.|LPVOID|
|`flags`|Reservado para uso futuro. Deve ser 0.|DWORD|

### <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um HRESULT que representa a falha. Se ocorrer uma exceção gerenciada, retornará 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Confira também
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>
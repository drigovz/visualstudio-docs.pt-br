---
title: Função SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4953c8478e25a1534691e99c41dce03930ac46ef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434671"
---
# <a name="sccdirqueryinfo-function"></a>Função SccDirQueryInfo
Essa função examina uma lista de diretórios totalmente qualificados para o seu status atual.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parâmetros
 pContext

[in] A estrutura de contexto de plug-in de controle de origem.

 nDirs

[in] O número de diretórios selecionados para serem consultados.

 lpDirNames

[in] Uma matriz de caminhos totalmente qualificados dos diretórios a serem consultadas.

 lpStatus

[no, out] Uma estrutura de matriz para o plug-in para retornar os sinalizadores de status de controle de origem (consulte [código de status do diretório](../extensibility/directory-status-code-enumerator.md) para obter detalhes).

## <a name="return-value"></a>Valor retornado
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A consulta foi bem-sucedida.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle do código-fonte não oferece suporte a essa operação.|
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção. É recomendável uma nova tentativa.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 A função preenche a matriz de retornada com uma máscara de bits de bits do `SCC_DIRSTATUS` família (consulte [código de status do diretório](../extensibility/directory-status-code-enumerator.md)), uma entrada para cada diretório fornecido. A matriz de status é alocada pelo chamador.

 O IDE usa essa função antes de um diretório é renomeado para verificar se o diretório está sob controle do código-fonte, consultando se ele tem um projeto correspondente. Se o diretório não está sob controle de origem, o IDE pode fornecer o aviso apropriado para o usuário.

> [!NOTE]
> Se um plug-in de controle do código-fonte optar por não implementar uma ou mais dos valores de status, o bits não implementadas devem ser definidos como zero.

## <a name="see-also"></a>Consulte também
- [Funções de API de plug-in da controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Código de status do diretório](../extensibility/directory-status-code-enumerator.md)
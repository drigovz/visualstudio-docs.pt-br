---
title: Função SccQueryInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f951e7ef29fbba7225997276b31bd9f32731efc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199980"
---
# <a name="sccqueryinfo-function"></a>Função SccQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função obtém informações de status para um conjunto de arquivos selecionados sob controle do código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 no A estrutura de contexto do plug-in de controle do código-fonte.  
  
 nFiles  
 no Número de arquivos especificados na `lpFileNames` matriz e o comprimento da `lpStatus` matriz.  
  
 lpFileNames  
 no Uma matriz de nomes de arquivos a serem consultados.  
  
 lpStatus  
 [entrada, saída] Uma matriz na qual o plug-in de controle do código-fonte retorna os sinalizadores de status para cada arquivo. Para obter mais informações, consulte [código de status do arquivo](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A consulta foi bem-sucedida.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente causado por problemas de rede ou de contenção. Uma nova tentativa é recomendada.|  
|SCC_E_PROJNOTOPEN|O projeto não está aberto sob controle do código-fonte.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Se `lpFileName` for uma cadeia de caracteres vazia, no momento não há informações de status para atualizar. Caso contrário, é o nome do caminho completo do arquivo para o qual as informações de status podem ter mudado.  
  
 A matriz de retorno pode ser um bitmask de `SCC_STATUS_xxxx` bits. Para obter mais informações, consulte [código de status do arquivo](../extensibility/file-status-code-enumerator.md). Um sistema de controle do código-fonte pode não dar suporte A todos os tipos de bits. Por exemplo, se `SCC_STATUS_OUTOFDATE` não for oferecido, o bit simplesmente não será definido.  
  
 Ao usar essa função para fazer check-out de arquivos, observe os seguintes `MSSCCI` requisitos de status:  
  
- `SCC_STATUS_OUTBYUSER` é definido quando o usuário atual fez o check-out do arquivo.  
  
- `SCC_STATUS_CHECKEDOUT` Não pode ser definido a menos que `SCC_STATUS_OUTBYUSER` esteja definido.  
  
- `SCC_STATUS_CHECKEDOUT` é definido apenas quando o check-out do arquivo é feito no diretório de trabalho designado.  
  
- Se o check-out do arquivo for feito pelo usuário atual em um diretório diferente do diretório de trabalho, o `SCC_STATUS_OUTBYUSER` será definido, mas `SCC_STATUS_CHECKEDOUT` não será.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de status do arquivo](../extensibility/file-status-code-enumerator.md)

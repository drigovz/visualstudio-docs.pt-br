---
title: Função SccDirDiff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81279e0fdb0df6600686adc57bb1c5489e8e7aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838279"
---
# <a name="sccdirdiff-function"></a>Função SccDirDiff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função exibe as diferenças entre o diretório local atual no disco do cliente e o projeto correspondente sob controle do código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 no A estrutura de contexto do plug-in de controle do código-fonte.  
  
 hWnd  
 no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.  
  
 lpDirName  
 no Caminho totalmente qualificado para o diretório local para o qual mostrar uma diferença visual.  
  
 dwFlags  
 no Sinalizadores de comando (consulte a seção comentários).  
  
 pvOptions  
 no Opções específicas de plug-ins de controle do código-fonte.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O diretório no disco é o mesmo que o projeto no controle do código-fonte.|  
|SCC_I_FILESDIFFER|O diretório em disco é diferente do projeto no controle do código-fonte.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTCONTROLLED|O diretório não está no controle do código-fonte.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção. Uma nova tentativa é recomendada.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
|SCC_E_FILENOTEXIST|Não foi possível encontrar o diretório local.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para instruir o plug-in de controle do código-fonte a exibir ao usuário uma lista de alterações em um diretório especificado. O plug-in abre sua própria janela, em um formato de sua escolha, para exibir as diferenças entre o diretório do usuário no disco e o projeto correspondente sob controle de versão.  
  
 Se um plug-in der suporte à comparação de diretórios, ele deverá dar suporte à comparação de diretórios em uma base de nome de arquivo mesmo que as opções de "diferença rápida" não tenham suporte.  
  
|`dwFlags`|Interpretação|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparação que não diferencia maiúsculas de minúsculas (pode ser usada para comparação rápida ou Visual).|  
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para comparação rápida ou Visual).|  
|SCC_DIFF_QD_CONTENTS|Se houver suporte do plug-in de controle do código-fonte, o compara o diretório, byte por byte, silenciosamente.|  
|SCC_DIFF_QD_CHECKSUM|Se houver suporte do plug-in, o compara silenciosamente o diretório por meio de uma soma de verificação ou, se não houver suporte, volta a SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Se houver suporte do plug-in, o compara silenciosamente o diretório por meio de seu carimbo de data/hora ou, se não houver suporte, voltará a SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
> Essa função usa os mesmos sinalizadores de comando que o [SccDiff](../extensibility/sccdiff-function.md). No entanto, um plug-in de controle do código-fonte pode optar por não oferecer suporte à operação de "comparação rápida" para diretórios.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)

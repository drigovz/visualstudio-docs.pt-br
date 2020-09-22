---
title: Função SccDiff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa5ea0a269cdbfe678328dc652b4177bdc667b99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838260"
---
# <a name="sccdiff-function"></a>Função SccDiff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função exibe (ou, opcionalmente, apenas verifica) as diferenças entre o arquivo atual (no disco local) e sua última versão com check-in no sistema de controle do código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 no A estrutura de contexto do plug-in de controle do código-fonte.  
  
 hWnd  
 no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.  
  
 lpFileName  
 no Nome do arquivo para o qual a diferença é solicitada.  
  
 fOptions  
 no Sinalizadores de comando. Consulte comentários para obter detalhes.  
  
 pvOptions  
 no Opções específicas de plug-ins de controle do código-fonte.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A cópia de trabalho e a versão do servidor são idênticas.|  
|SCC_I_FILESDIFFERS|A cópia de trabalho difere da versão no controle do código-fonte.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTCONTROLLED|O arquivo não está no controle do código-fonte.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção. Uma nova tentativa é recomendada.|  
|SCC_E_NONSPECIFICERROR|Falha não específica; diferença de arquivo não obtida.|  
|SCC_E_FILENOTEXIST|O arquivo local não foi encontrado.|  
  
## <a name="remarks"></a>Comentários  
 Essa função atende a duas finalidades diferentes. Por padrão, ele exibe uma lista de alterações em um arquivo. O plug-in de controle do código-fonte abre sua própria janela, em qualquer formato que escolher, para exibir as diferenças entre o arquivo do usuário no disco e a versão mais recente do arquivo sob controle do código-fonte.  
  
 Como alternativa, o IDE pode simplesmente precisar determinar se um arquivo foi alterado. Por exemplo, o IDE pode precisar determinar se é seguro fazer check-out de um arquivo sem informar o usuário. Nesse caso, o IDE passa o `SCC_DIFF_CONTENTS` sinalizador. O plug-in de controle do código-fonte deve verificar o arquivo em disco, byte por byte, em relação ao arquivo de origem controlada e retornar um valor que indica se os dois arquivos são diferentes sem exibir nada para o usuário.  
  
 Como uma otimização de desempenho, o plug-in de controle do código-fonte pode usar uma alternativa com base em uma soma de verificação ou em um carimbo de data/hora, em vez da comparação byte a byte chamada para `SCC_DIFF_CONTENTS` : essas formas de comparação são obviamente mais rápidas, mas menos confiáveis. Nem todos os sistemas de controle do código-fonte podem dar suporte a esses métodos de comparação alternativos, e o plug-in pode ter que fazer fallback para uma comparação de conteúdo. Todos os plug-ins de controle do código-fonte devem, no mínimo, dar suporte a uma comparação de conteúdo.  
  
> [!NOTE]
> Os sinalizadores de diferença rápida são mutuamente exclusivos. Ele é válido para não passar nenhum sinalizador, mas não é válido para passar mais de um simultaneamente. `SCC_DIFF_QUICK_DIFF`, que é uma máscara que combina todos os sinalizadores, pode ser usada para testar, mas ele nunca deve ser passado como um parâmetro.  
  
|`fOption`|Significado|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Comparação que não diferencia maiúsculas de minúsculas (pode ser usada para diferença rápida ou Visual).|  
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para diferença rápida ou Visual).|  
|SCC_DIFF_QD_CONTENTS|Compara silenciosamente o arquivo, byte por byte.|  
|SCC_DIFF_QD_CHECKSUM|Compara silenciosamente o arquivo por meio de uma soma de verificação quando há suporte. Se não houver suporte, retorne para uma comparação de conteúdo.|  
|SCC_DIFF_QD_TIME|Compara silenciosamente o arquivo por meio de seu carimbo de data/hora quando há suporte. Se não houver suporte, retorne para uma comparação de conteúdo.|  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)

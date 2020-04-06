---
title: Função SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701029"
---
# <a name="sccdiff-function"></a>Função SccDiff
Esta função exibe (ou opcionalmente apenas verifica) as diferenças entre o arquivo atual (no disco local) e sua última versão de check-in no sistema de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 Lpfilename

[em] Nome do arquivo para o qual a diferença é solicitada.

 fOpções

[em] Bandeiras de comando. Consulte observações para obter detalhes.

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A cópia de trabalho e a versão do servidor são idênticas.|
|SCC_I_FILESDIFFERS|A cópia de trabalho difere da versão sob controle de origem.|
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|
|SCC_E_FILENOTCONTROLLED|O arquivo não está sob controle de origem.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECIFICERROR|Falha não específica; a diferença de arquivos não foi obtida.|
|SCC_E_FILENOTEXIST|O arquivo local não foi encontrado.|

## <a name="remarks"></a>Comentários
 Esta função serve a dois propósitos diferentes. Por padrão, ele exibe uma lista de alterações em um arquivo. O plug-in de controle de origem abre sua própria janela, em qualquer formato que escolher, para exibir as diferenças entre o arquivo do usuário em disco e a versão mais recente do arquivo sob controle de origem.

 Alternativamente, o IDE pode simplesmente precisar determinar se um arquivo foi alterado. Por exemplo, o IDE pode precisar determinar se é seguro verificar um arquivo sem informar o usuário. Nesse caso, o IDE `SCC_DIFF_CONTENTS` passa na bandeira. O plug-in de controle de origem deve verificar o arquivo em disco, byte byte, contra o arquivo controlado por origem e retornar um valor indicando se os dois arquivos são diferentes sem exibir nada ao usuário.

 Como uma otimização de desempenho, o plug-in de controle de origem pode usar uma alternativa baseada em um `SCC_DIFF_CONTENTS`soma de verificação ou um carimbo de tempo em vez da comparação byte-by-byte solicitada por : essas formas de comparação são obviamente mais rápidas, mas menos confiáveis. Nem todos os sistemas de controle de origem podem suportar esses métodos alternativos de comparação, e o plug-in pode ter que voltar a uma comparação de conteúdo. Todos os plug-ins de controle de origem devem, no mínimo, suportar uma comparação de conteúdo.

> [!NOTE]
> As bandeiras de diferença rápida são mutuamente exclusivas. É válido não passar bandeiras, mas não é válido passar simultaneamente mais de uma. `SCC_DIFF_QUICK_DIFF`, que é uma máscara que combina todas as bandeiras, pode ser usada para testar, mas nunca deve ser passada como parâmetro.

|`fOption`|Significado|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Comparação insensível a casos (pode ser usada para diferença rápida ou visual).|
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para diferença rápida ou visual).|
|SCC_DIFF_QD_CONTENTS|Silenciosamente compara o arquivo, byte byte.|
|SCC_DIFF_QD_CHECKSUM|Silenciosamente compara o arquivo através de uma soma de cheques quando suportado. Se não for suportado, recua para uma comparação de conteúdo.|
|SCC_DIFF_QD_TIME|Silenciosamente compara o arquivo através de seu carimbo de tempo quando suportado. Se não for suportado, recua para uma comparação de conteúdo.|

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)

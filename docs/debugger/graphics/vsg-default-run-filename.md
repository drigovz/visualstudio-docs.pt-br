---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af34aed1ed99e1d8e51e594a514286caa7adf748
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979914"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Define o nome de arquivo padrão do arquivo de log de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `filename`  
 O nome do arquivo fornecido por padrão para o arquivo de log de gráficos quando informações de gráficos são capturadas por meio de programação.  
  
## <a name="value"></a>Valor  
 Arquivo de log de uma cadeia de caracteres literal que representa o nome de arquivo dos elementos gráficos. Por padrão, L"default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Comentários  
 Se o símbolo do pré-processador `DONT_SAVE_VSGLOG_TO_TEMP` é definido, em seguida, o nome do arquivo é relativo ao diretório atual do aplicativo capturado, ou é um caminho absoluto; caso contrário, ele é relativo ao diretório de arquivos temporários do usuário e não pode ser um caminho absoluto.  
  
 Para alterar o nome do arquivo definidos, você deve redefini-la antes de incluir `vsgcapture.h` em seu programa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como alterar o nome de arquivo padrão do arquivo de captura:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Consulte também  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
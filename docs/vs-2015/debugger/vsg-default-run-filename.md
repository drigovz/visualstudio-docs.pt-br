---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160767"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define o nome de arquivo padrão do arquivo de log de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `filename`  
 O nome de arquivo fornecido por padrão para o arquivo de log de gráficos quando as informações gráficas são capturadas programaticamente.  
  
## <a name="value"></a>Valor  
 Um literal de cadeia de caracteres que representa o nome de arquivo do arquivo de log de gráficos. Por padrão, L "default. vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Comentários  
 Se o símbolo de pré-processador `DONT_SAVE_VSGLOG_TO_TEMP` for definido, o nome do arquivo será relativo ao diretório atual do aplicativo capturado, ou é um caminho absoluto; caso contrário, ele é relativo ao diretório de arquivos temporários do usuário e não pode ser um caminho absoluto.  
  
 Para alterar o nome de arquivo definido, você deve redefini-lo antes `vsgcapture.h` de incluir em seu programa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como alterar o nome de arquivo padrão do arquivo de captura:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)

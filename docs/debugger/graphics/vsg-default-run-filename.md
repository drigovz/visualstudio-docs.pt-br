---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8aff9836570b3af882e5863cc85834f5423f890e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861420"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Define o nome de arquivo padrão do arquivo de log de gráficos.

## <a name="syntax"></a>Sintaxe

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parâmetros
 `filename` O nome de arquivo fornecido por padrão para o arquivo de log de gráficos quando as informações gráficas são capturadas programaticamente.

## <a name="value"></a>Valor
 Um literal de cadeia de caracteres que representa o nome de arquivo do arquivo de log de gráficos. Por padrão, L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Comentários
 Se o símbolo de pré-processador `DONT_SAVE_VSGLOG_TO_TEMP` for definido, o nome do arquivo será relativo ao diretório atual do aplicativo capturado, ou é um caminho absoluto; caso contrário, ele é relativo ao diretório de arquivos temporários do usuário e não pode ser um caminho absoluto.

 Para alterar o nome de arquivo definido, você deve redefini-lo antes `vsgcapture.h` de incluir em seu programa.

## <a name="example"></a>Exemplo
 Este exemplo mostra como alterar o nome de arquivo padrão do arquivo de captura:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Consulte também
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
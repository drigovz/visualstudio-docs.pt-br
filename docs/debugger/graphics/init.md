---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734998"
---
# <a name="init"></a>Init
Prepara o componente no aplicativo do diagnóstico de gráficos para capturar e gravar ativamente informações de gráficos em um arquivo de log de gráficos.

## <a name="syntax"></a>Sintaxe

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parâmetros
 `vsgLogGetter` uma entidade que possa ser chamada, como uma função, um ponteiro de função, lambda ou um objeto de função — que usa como parâmetros o comprimento de um buffer composto por `wchar_t` e um ponteiro para esse buffer e retorna `void`. Quando invocado, a entidade callable determina o nome do arquivo que será usado para registrar informações gráficas e grava-o no buffer especificado antes de retornar.

## <a name="remarks"></a>Comentários
 A função `Init` é chamada automaticamente quando uma instância da classe `VsgDbg` é construída especificando o parâmetro `bDefaultInit` de seu construtor como `true`; caso contrário, `Init` deve ser chamado explicitamente antes que você possa capturar e registrar informações de gráficos ativamente.

 Você pode finalizar e fechar o arquivo de log de gráficos ativo chamando `UnInit` e, em seguida, capturar e registrar mais informações sobre gráficos em um novo arquivo de log de gráficos chamando `Init` novamente. Você pode repetir isso quantas vezes desejar para criar vários arquivos de log de gráficos independentes usando a mesma instância de `VsgDbg`.

## <a name="see-also"></a>Consulte também
- [UnInit](init.md)
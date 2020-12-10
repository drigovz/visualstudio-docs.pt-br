---
title: Init | Microsoft Docs
description: Use o método init () de VsgDbg para preparar o componente no aplicativo de diagnóstico de gráficos para registrar informações de gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 094f4f3c64570a0af5396e903541c70a919cc0d3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996182"
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
 `vsgLogGetter` Uma entidade que possa ser chamada, como uma função, um ponteiro de função, lambda ou um objeto de função — que usa como parâmetros o comprimento de um buffer composto `wchar_t` e um ponteiro para esse buffer, e retorna `void` . Quando invocado, a entidade callable determina o nome do arquivo que será usado para registrar informações gráficas e grava-o no buffer especificado antes de retornar.

## <a name="remarks"></a>Comentários
 A `Init` função é chamada automaticamente quando uma instância da `VsgDbg` classe é construída especificando o `bDefaultInit` parâmetro de seu construtor como `true` ; caso contrário, `Init` deve ser chamado explicitamente antes que você possa capturar e registrar informações de gráficos ativamente.

 Você pode finalizar e fechar o arquivo de log de gráficos ativo chamando e `UnInit` , em seguida, capturar e registrar mais informações sobre gráficos em um novo arquivo de log de gráficos chamando `Init` novamente. Você pode repetir isso quantas vezes desejar para criar vários arquivos de log de gráficos independentes usando a mesma `VsgDbg` instância.

## <a name="see-also"></a>Confira também
- [UnInit](init.md)
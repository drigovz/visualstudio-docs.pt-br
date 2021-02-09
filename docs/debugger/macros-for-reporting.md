---
title: Macros para relatórios | Microsoft Docs
description: Saiba mais sobre as macros de depuração _RPTn e _RPTFn fornecidas no CRTDBG. H e sobre como criar suas próprias macros de depuração.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0356f05c3f0dac636813d1632f628dd02dd28923
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893120"
---
# <a name="macros-for-reporting"></a>Macros para relatórios
Para depuração, você pode usar as macros **_RPTn** e **_RPTFn** , definidas em CRTDBG. H, para substituir o uso de `printf` instruções. Você não precisa infechá-los em **#ifdef** s, pois eles desaparecerão automaticamente em sua compilação de versão quando **_DEBUG** não estiver definido.

|Macro|Descrição|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Gera uma cadeia de caracteres de mensagem e zero a quatro argumentos. Por **_RPT1** por meio de **_RPT4**, a cadeia de caracteres de mensagem serve como uma cadeia de caracteres de formatação de estilo printf para os argumentos.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|Da mesma forma que **_RPTn**, mas essas macros também geram a saída do nome do arquivo e o número da linha em que a macro está localizada.|

 Considere o seguinte exemplo:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Esse código gera os valores de `someVar` e `otherVar` a **stdout**. Você pode usar a seguinte chamada para `_RPTF2` para reportar os mesmos valores e, além disso, o nome de arquivo e o número de linha:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Você pode achar que um aplicativo específico precisa de relatórios de depuração de que as macros fornecidas com a biblioteca de tempo de execução C não fornecem. Nesses casos, você pode escrever uma macro projetada especificamente para atender aos seus próprios requisitos. Em um dos arquivos de cabeçalho, por exemplo, você pode incluir código como o seguinte para definir uma macro chamada **ALERT_IF2**:

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 Uma chamada para **ALERT_IF2** poderia fazer todas as funções do código **printf** :

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Você pode alterar facilmente uma macro personalizada para relatar mais ou menos informações para destinos diferentes. Essa abordagem é particularmente útil à medida que os requisitos de depuração evoluem.

## <a name="see-also"></a>Confira também
- [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)

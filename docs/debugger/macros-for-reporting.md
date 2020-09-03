---
title: Macros para relatórios | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2129db98293cef678527fb331992c6c5960d8f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731383"
---
# <a name="macros-for-reporting"></a>Macros para relatórios
Para depuração, você pode usar as macros **_RPTn** e **_RPTFn** , definidas em CRTDBG. H, para substituir o uso de `printf` instruções. Você não precisa infechá-los em **#ifdef**s, pois eles desaparecerão automaticamente em sua compilação de versão quando **_DEBUG** não estiver definido.

|Macro|Descrição|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Gera uma cadeia de caracteres de mensagem e zero a quatro argumentos. Para _RPT1 até **_RPT4**, a cadeia de caracteres de mensagem funciona como uma cadeia de caracteres de formatação de estilo printf para os argumentos.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Da mesma forma que **_RPTn**, mas essas macros também geram a saída do nome do arquivo e o número da linha em que a macro está localizada.|

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

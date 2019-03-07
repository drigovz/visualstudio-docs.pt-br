---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f02545f1c19b57e46af302fbc0b2abaa7445612
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646337"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Especifica a linguagem de código fonte do aplicativo ou módulo vinculado.

## <a name="syntax"></a>Sintaxe

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Elementos
Idioma do aplicativo CV_CFL_C é C.

Idioma do aplicativo CV_CFL_CXX é C++.

Idioma do aplicativo CV_CFL_FORTRAN é FORTRAN.

Idioma do aplicativo CV_CFL_MASM é Microsoft Macro Assembler.

Idioma do aplicativo CV_CFL_PASCAL é Pascal.

Idioma do aplicativo CV_CFL_BASIC é BASIC.

Idioma do aplicativo CV_CFL_COBOL é COBOL.

Aplicativo CV_CFL_LINK é um módulo geradas pelo vinculador.

Aplicativo CV_CFL_CVTRES é um módulo de recurso convertido com a ferramenta CVTRES.

Aplicativo CV_CFL_CVTPGD é um módulo POGO otimizado gerado com a ferramenta CVTPGD.

Idioma do aplicativo CV_CFL_CSHARP é C#.

Idioma do aplicativo CV_CFL_VB é o Visual Basic.

Idioma do aplicativo CV_CFL_ILASM é o assembly de linguagem intermediária (ou seja, o assembly do Common Language Runtime (CLR)).

Idioma do aplicativo CV_CFL_JAVA é Java.

Idioma do aplicativo CV_CFL_JSCRIPT é Jscript.

Idioma do aplicativo CV_CFL_MSIL é um desconhecido MSIL Microsoft Intermediate Language (), possivelmente um resultado do uso de [/LTCG (geração de código Link-time)](/cpp/build/reference/ltcg-link-time-code-generation) alternar.

Idioma do aplicativo CV_CFL_HLSL é a linguagem de sombreador alta.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados por uma chamada para o [idiasymbol:: Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)

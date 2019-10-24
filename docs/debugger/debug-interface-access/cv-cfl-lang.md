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
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745344"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Especifica o idioma do código-fonte do aplicativo ou módulo vinculado.

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
O idioma do aplicativo CV_CFL_C é C.

O idioma do aplicativo C++CV_CFL_CXX é.

O idioma do aplicativo CV_CFL_FORTRAN é o FORTRAN.

O idioma do aplicativo CV_CFL_MASM é o Microsoft Macro Assembler.

O idioma do aplicativo CV_CFL_PASCAL é Pascal.

O idioma do aplicativo CV_CFL_BASIC é básico.

O idioma do aplicativo CV_CFL_COBOL é COBOL.

O aplicativo CV_CFL_LINK é um módulo gerado pelo vinculador.

O aplicativo CV_CFL_CVTRES é um módulo de recurso convertido com a ferramenta CVTRES.

O aplicativo CV_CFL_CVTPGD é um módulo do POGO Optimized gerado com a ferramenta CVTPGD.

O idioma do aplicativo C#CV_CFL_CSHARP é.

O idioma do aplicativo CV_CFL_VB é Visual Basic.

O idioma do aplicativo CV_CFL_ILASM é um assembly de linguagem intermediária (ou seja, o Common Language Runtime (CLR) assembly).

O idioma do aplicativo CV_CFL_JAVA é Java.

O idioma do aplicativo CV_CFL_JSCRIPT é JScript.

O idioma do aplicativo CV_CFL_MSIL é uma MSIL (Microsoft Intermediate Language) desconhecida, possivelmente um resultado do uso da opção [/LTCG (geração de código de tempo de vinculação)](/cpp/build/reference/ltcg-link-time-code-generation) .

O idioma do aplicativo CV_CFL_HLSL é uma linguagem de sombreamento de alto nível.

## <a name="remarks"></a>Comentários
Os valores nessa enumeração são retornados por uma chamada para o método [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)

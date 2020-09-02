---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699354"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica o idioma do código-fonte do aplicativo ou módulo vinculado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 CV_CFL_C  
 O idioma do aplicativo é C.  
  
 CV_CFL_CXX  
 O idioma do aplicativo é C++.  
  
 CV_CFL_FORTRAN  
 O idioma do aplicativo é o FORTRAN.  
  
 CV_CFL_MASM  
 O idioma do aplicativo é o Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 O idioma do aplicativo é Pascal.  
  
 CV_CFL_BASIC  
 O idioma do aplicativo é básico.  
  
 CV_CFL_COBOL  
 O idioma do aplicativo é COBOL.  
  
 CV_CFL_LINK  
 O aplicativo é um módulo gerado pelo vinculador.  
  
 CV_CFL_CVTRES  
 O aplicativo é um módulo de recurso convertido com a ferramenta CVTRES.  
  
 CV_CFL_CVTPGD  
 Application é um módulo do POGO Optimized gerado com a ferramenta CVTPGD.  
  
 CV_CFL_CSHARP  
 O idioma do aplicativo é C#.  
  
 CV_CFL_VB  
 O idioma do aplicativo é Visual Basic.  
  
 CV_CFL_ILASM  
 O idioma do aplicativo é um assembly de linguagem intermediária (ou seja, assembly CLR).  
  
 CV_CFL_JAVA  
 O idioma do aplicativo é Java.  
  
 CV_CFL_JSCRIPT  
 O idioma do aplicativo é JScript.  
  
 CV_CFL_MSIL  
 O idioma do aplicativo é uma MSIL (Microsoft Intermediate Language) desconhecida, possivelmente um resultado do uso da opção [/LTCG (geração de código de tempo de vinculação)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 O idioma do aplicativo é uma linguagem de sombreamento de alto nível.  
  
## <a name="remarks"></a>Comentários  
 Os valores nessa enumeração são retornados por uma chamada para o método [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst. h  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)

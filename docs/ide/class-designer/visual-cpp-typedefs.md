---
title: TYPEDEFs C++ no Designer de Classe
description: Saiba mais sobre como Designer de Classe dá suporte a tipos de typedef C++ declarados com o typedef de palavra-chave.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: b50b4be5552b3c6a0ba965b97aa2e1668a7369d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954456"
---
# <a name="c-typedefs-in-class-designer"></a>TYPEDEFs C++ no Designer de Classe

Instruções [typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) criam uma ou mais camadas de indireção entre um nome e seu tipo subjacente. O **Designer de Classe** é compatível com tipos de typedef do C++ declarados com a palavra-chave `typedef`, por exemplo:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Então, você pode usar esse tipo para declarar uma instância:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Formas de classe e de struct

No **Designer de Classe**, um typedef do C++ tem a forma do tipo especificado no typedef. Se a fonte declarar `typedef class`, a forma terá cantos arredondados e o rótulo **Classe**. Para `typedef struct`, a forma tem cantos quadrados e o rótulo **Struct**.

Classes e estruturas podem ter typedefs aninhados declarados dentro delas. No **Designer de Classe**, formas de classe e de estrutura podem mostrar declarações de typedef aninhado como formas aninhadas.

As formas typedef oferecem suporte aos comandos **Mostrar como Associação** e **Mostrar como Associação de Coleções** no menu do clique com o botão direito (menu de contexto).

### <a name="class-typedef-example"></a>Exemplo do typedef de classe

```cpp
class B {};
typedef B MyB;
```

![Typedef de classe do C++ no Designer de Classe](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Exemplo do typedef de struct

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Typedef de struct do C++ no Designer de Classe](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Typedefs sem nome

Embora seja possível declarar um typedef sem um nome, o **Designer de Classe** não usará o nome da marca especificada. O **Designer de Classe** use o nome gerado pelo **Modo de Exibição de Classe**. Por exemplo, a declaração a seguir é válida, mas aparece em **modo de exibição de classe** e **Designer de classe** como um objeto chamado **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> O **Designer de Classe** não exibe typedefs cujo tipo de origem é um ponteiro de função.

## <a name="see-also"></a>Confira também

- [Trabalhar com código C++](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)

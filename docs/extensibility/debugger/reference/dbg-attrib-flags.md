---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c8b3f52eff80c187d3c43b87cea804ace483169
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737550"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Descreve vários atributos para uma [interface IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md) Membro da estrutura [DEBUG_PROPERTY_INFO.](../../../extensibility/debugger/reference/debug-property-info.md)

## <a name="syntax"></a>Sintaxe

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Membros
 `DBG_ATTRIB_NONE`\
 Indica nenhum atributo.

 `DBG_ATTRIB_ALL`\
 Indica todos os atributos.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Indica que a propriedade ou referência tem filhos.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Indica que um ID para este objeto foi criado.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Indica que um ID para este objeto pode ser criado.

 `DBG_ATTRIB_VALUE_READONLY`\
 Indica que o valor é somente leitura.

 `DBG_ATTRIB_VALUE_ERROR`\
 Indica que o valor é um erro.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Indica que a avaliação teve um efeito colateral.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Indica que esta propriedade é realmente um contêiner de sobrecargas.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Indica que o `DEBUG_PROPERTY_INFO::bstrValue` valor é booleano.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Indica que o `DEBUG_PROPERTY_INFO::bstrValue` valor é `TRUE`booleano e .

 `DBG_ATTRIB_VALUE_INVALID`\
 Indica que o valor no `DEBUG_PROPERTY_INFO::bstrValue` não é válido.

 `DBG_ATTRIB_VALUE_NAT`\
 Indica que o `DEBUG_PROPERTY_INFO::bstrValue` valor em é "*não uma coisa*" (NAT). O NAT descreve um sinalizador de registro em processadores Intel de 64 bits que indica exceções especulativas diferidas.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Indica que o `DEBUG_PROPERTY_INFO::bstrValue` valor foi possivelmente expandido automaticamente.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Indica que uma avaliação tem tempo.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Indica que o `DEBUG_PROPERTY_INFO::bstrValue` valor em pode ser representado por uma seqüência bruta.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Indica que esta propriedade tem pelo menos um visualizador personalizado associado a ela.

 `DBG_ATTRIB_ACCESS_NONE`\
 Indica um objeto `public`que `private`não `protected` tem acesso, nem digite.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Indica um objeto que tem acesso público.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Indica um objeto que tem acesso privado.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Indica um objeto que tem acesso protegido.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Indica um objeto que tem acesso final.

 `DBG_ATTRIB_ACCESS_ALL`\
 Máscara para extrair os `DBG_ATTRIB_FLAGS`atributos de acesso de .

 `DBG_ATTRIB_STORAGE_NONE`\
 Indica que não há nenhum tipo de armazenamento especificado.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Indica o armazenamento global.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Indica o armazenamento estático.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Indica armazenamento no caixa.

 `DBG_ATTRIB_STORAGE_ALL`\
 Máscara para extrair os `DBG_ATTRIB_FLAGS`atributos de armazenamento de .

 `DBG_ATTRIB_TYPE_NONE`\
 Indica que não há modificador de tipo.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Indica que o tipo de objeto é virtual.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Indica que o tipo de objeto é constante.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Indica que o tipo de objeto está sincronizado.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Indica que o tipo de objeto é volátil.

 `DBG_ATTRIB_TYPE_ALL`\
 Máscara para extrair os `DBG_ATTRIB_FLAGS`atributos do tipo de .

 `DBG_ATTRIB_DATA`\
 Indica que este objeto é um campo de dados.

 `DBG_ATTRIB_METHOD`\
 Indica que este objeto é um método.

 `DBG_ATTRIB_PROPERTY`\
 Indica que este objeto é uma propriedade.

 `DBG_ATTRIB_CLASS`\
 Indica que este objeto é uma classe.

 `DBG_ATTRIB_BASECLASS`\
 Indica que este objeto é uma classe base.

 `DBG_ATTRIB_INTERFACE`\
 Indica que este objeto é uma interface.

 `DBG_ATTRIB_INNERCLASS`\
 Indica que este objeto é uma classe interna.

 `DBG_ATTRIB_MOSTDERIVED`\
 Indica que este objeto é '*mais derivado*'. O termo "*mais derivado*" significa o tipo real do objeto, e não o tipo de sua referência.

 `DBG_ATTRIB_CHILD_ALL`\
 Indica uma `DBG_ATTRIB_DATA` máscara `DBG_ATTRIB_MOSTDERIVED`de passagem.

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Indica que o objeto tem vários visualizaes personalizados associados a ele.

## <a name="remarks"></a>Comentários

> [!NOTE]
> Os valores nesta enumeração não são realmente definidos na montagem para C#. Em vez disso, você deve copiar as definições para o seu arquivo de origem.

 Essas bandeiras também são usadas para filtrar crianças de um objeto, por exemplo, quando passadas como argumento para [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Os valores podem ser combinados com um pouco `OR`.

 O `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` sinalizador é [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uma indicação para obter a interface [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) da interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) e chamar [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para uma lista de espectadores personalizados.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

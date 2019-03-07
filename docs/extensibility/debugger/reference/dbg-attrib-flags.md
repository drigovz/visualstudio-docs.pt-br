---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 831d1326d88e70ffaba2cc0c242c55d7325be705
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689324"
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Descreve vários atributos para um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ou um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interface. Membro de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estrutura.

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
 DBG_ATTRIB_NONE não indica nenhum atributo.

 DBG_ATTRIB_ALL indica todos os atributos.

 DBG_ATTRIB_OBJ_IS_EXPANDABLE indica que a propriedade ou referência tem filhos.

 DBG_ATTRIB_OBJ_HAS_ID indica que uma ID para esse objeto foi criada.

 DBG_ATTRIB_OBJ_CAN_HAVE_ID indica que uma ID para esse objeto pode ser criada.

 DBG_ATTRIB_VALUE_READONLY indica que o valor é somente leitura.

 DBG_ATTRIB_VALUE_ERROR indica que o valor é um erro.

 DBG_ATTRIB_VALUE_SIDE_EFFECT indica que a avaliação de um efeito colateral.

 DBG_ATTRIB_OVERLOADED_CONTAINER indica que essa propriedade é realmente um contêiner de sobrecargas.

 DBG_ATTRIB_VALUE_BOOLEAN indica que o valor em `DEBUG_PROPERTY_INFO::bstrValue` é booliano.

 DBG_ATTRIB_VALUE_BOOLEAN_TRUE indica que o valor em `DEBUG_PROPERTY_INFO::bstrValue` é booliano e `TRUE`.

 DBG_ATTRIB_VALUE_INVALID indica que o valor em `DEBUG_PROPERTY_INFO::bstrValue` não é válido.

 DBG_ATTRIB_VALUE_NAT indica que o valor em `DEBUG_PROPERTY_INFO::bstrValue` é "*nada*" (NAT). NAT descreve um sinalizador de registro em processadores Intel de 64 bits que indica exceções especulativas adiadas.

 DBG_ATTRIB_VALUE_AUTOEXPANDED indica que o valor em `DEBUG_PROPERTY_INFO::bstrValue` possivelmente foi expandido para automático.

 DBG_ATTRIB_VALUE_TIMEOUT indica que uma avaliação foi excedido.

 DBG_ATTRIB_VALUE_RAW_STRING indica que o valor em `DEBUG_PROPERTY_INFO::bstrValue` pode ser representado por uma cadeia de caracteres bruta.

 DBG_ATTRIB_VALUE_CUSTOM_VIEWER indica que essa propriedade tem pelo menos um visualizador personalizado associado a ele.

 DBG_ATTRIB_ACCESS_NONE indica um objeto que não possui `public`, `private`, nem `protected` tipo de acesso.

 DBG_ATTRIB_ACCESS_PUBLIC indica um objeto que tem acesso público.

 DBG_ATTRIB_ACCESS_PRIVATE indica um objeto que tem acesso privado.

 DBG_ATTRIB_ACCESS_PROTECTED indica um objeto que tenha acesso protegido.

 DBG_ATTRIB_ACCESS_FINAL indica um objeto que tem acesso final.

 Atributos de máscara DBG_ATTRIB_ACCESS_ALL para extrair o acesso de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_STORAGE_NONE indica que não há nenhum tipo de armazenamento especificado.

 Indica DBG_ATTRIB_STORAGE_GLOBAL armazenamento global.

 Armazenamento estático DBG_ATTRIB_STORAGE_STATIC indica.

 Armazenamento DBG_ATTRIB_STORAGE_REGISTER indica no registro.

 Máscara de DBG_ATTRIB_STORAGE_ALL para extrair o armazenamento de atributos de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_TYPE_NONE indica que não há nenhum modificador de tipo.

 DBG_ATTRIB_TYPE_VIRTUAL indica que o tipo de objeto é virtual.

 DBG_ATTRIB_TYPE_CONSTANT indica que o tipo de objeto é constante.

 DBG_ATTRIB_TYPE_SYNCHRONIZED indica que o tipo de objeto é sincronizado.

 DBG_ATTRIB_TYPE_VOLATILE indica que o tipo de objeto é volátil.

 Máscara de DBG_ATTRIB_TYPE_ALL para extrair o tipo de atributos de `DBG_ATTRIB_FLAGS`.

 DBG_ATTRIB_DATA indica que esse objeto é um campo de dados.

 DBG_ATTRIB_METHOD indica que esse objeto é um método.

 DBG_ATTRIB_PROPERTY indica que esse objeto é uma propriedade.

 DBG_ATTRIB_CLASS indica que esse objeto é uma classe.

 DBG_ATTRIB_BASECLASS indica que esse objeto é uma classe base.

 DBG_ATTRIB_INTERFACE indica que esse objeto é uma interface.

 DBG_ATTRIB_INNERCLASS indica que esse objeto é uma classe interna.

 DBG_ATTRIB_MOSTDERIVED indica que esse objeto é '*mais derivado*'. O termo "*mais derivado*" significa que o tipo real do objeto e não o tipo de sua referência.

 DBG_ATTRIB_CHILD_ALL indica uma máscara de `DBG_ATTRIB_DATA` por meio de `DBG_ATTRIB_MOSTDERIVED`.

 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS indica que o objeto tem vários visualizadores personalizados associados a ele.

## <a name="remarks"></a>Comentários

> [!NOTE]
>  Os valores nesta enumeração, na verdade, não são definidos no assembly para c#. Em vez disso, você deve copiar as definições para seu arquivo de origem.

 Esses sinalizadores também são usados para filtrar o filho de um objeto, por exemplo, quando passado como um argumento para [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Os valores podem ser combinados com um bit a bit `OR`.

 O `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` sinalizador é uma indicação ao [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para obter o [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) da interface do [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface e chamada [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) para obter uma lista de visualizadores personalizados.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
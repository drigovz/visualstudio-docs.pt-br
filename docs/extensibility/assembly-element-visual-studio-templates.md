---
title: Elemento de montagem (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740037"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento de montagem (modelos do Visual Studio)
Especifica informações sobre um conjunto, que o modelo usa para adicionar uma referência dessa montagem aos projetos.

 \<VSTemplate \<>ModeloConteúdo \<> \<Referências \<>> de> de>

## <a name="syntax"></a>Sintaxe

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Referência](../extensibility/reference-element-visual-studio-templates.md)|Especifica a referência de montagem para adicionar quando o item é adicionado a um projeto.|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 Este texto especifica o conjunto para adicionar a um projeto quando o modelo de item é instanciado. Este nome de montagem deve ser especificado de uma das seguintes maneiras:

- Como um nome de assembléia completo. Por exemplo:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Como simples referência de texto. Por exemplo:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Comentários
 `Assembly`é um elemento `Reference`filho necessário de .

 Os `Reference` `References,` elementos `Assembly` e elementos só podem ser usados `Item`em arquivos *.vstemplate* que tenham um `Type` valor de atributo de .

## <a name="example"></a>Exemplo
 O exemplo a `TemplateContent` seguir ilustra o elemento de um modelo de item. Este XML adiciona referências aos conjuntos *System.dll* e *System.Data.dll.*

```
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Confira também
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)

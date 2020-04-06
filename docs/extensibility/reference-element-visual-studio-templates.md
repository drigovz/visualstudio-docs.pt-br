---
title: Elemento de referência (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701622"
---
# <a name="reference-element-visual-studio-templates"></a>Elemento de referência (modelos do Visual Studio)
Especifica a referência de montagem para adicionar quando o item é adicionado a um projeto.

 \<VSTemplate \<>TemplateReferências de> \<de referência> \<> de referência

## <a name="syntax"></a>Sintaxe

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Especifica informações sobre um conjunto, que o modelo usa para adicionar uma referência dessa montagem aos projetos. Deve haver `Assembly` um elemento `Reference` em cada elemento.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Referências](../extensibility/references-element-visual-studio-templates.md)|Agrupa as referências de montagem que o modelo adiciona aos projetos.|

## <a name="remarks"></a>Comentários
 `Reference`é um elemento `References`filho necessário de .

 Os `Reference` `References` elementos e elementos só podem ser `Type` usados `Item`em arquivos *.vstemplate* que tenham um valor de atributo de .

## <a name="example"></a>Exemplo
 O exemplo a `TemplateContent` seguir ilustra o elemento de um modelo de item. Este XML adiciona referências aos conjuntos *System.dll* e *System.Data.dll.*

```xml
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

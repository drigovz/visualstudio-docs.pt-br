---
title: Elemento PreviewImage (modelos do Visual Studio) | Microsoft Docs
description: Saiba mais sobre o elemento PreviewImage e como ele especifica o nome do arquivo para a imagem de visualização que será exibida na caixa de diálogo novo projeto ou adicionar novo item.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 326588259203224d3f70b505af8437af22930faa
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672340"
---
# <a name="previewimage-element-visual-studio-templates"></a>Elemento PreviewImage (modelos do Visual Studio)
Especifica a imagem de visualização, como um nome de arquivo, para a imagem de visualização que aparecerá na caixa de diálogo **novo projeto** ou **Adicionar novo item** .

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Sintaxe

```
<PreviewImage>"filename"</PreviewImage>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 nenhuma.

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto deve ser uma cadeia de caracteres que represente um nome de arquivo.

## <a name="remarks"></a>Comentários
 `PreviewImage` é um elemento opcional.

## <a name="see-also"></a>Veja também
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e item](../ide/creating-project-and-item-templates.md)

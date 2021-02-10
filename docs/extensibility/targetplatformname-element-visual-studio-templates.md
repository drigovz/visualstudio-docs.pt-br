---
title: Elemento TargetPlatformName (modelos do Visual Studio) | Microsoft Docs
description: Saiba mais sobre o elemento TargetPlatformName e como ele especifica a plataforma com a qual o modelo de projeto se destina.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f2b8903c99e5bd2f62587b7921be855e4ed6323
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938766"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>Elemento TargetPlatformName (Modelos do Visual Studio)
Especifica a plataforma de destino do modelo de projeto. Esse elemento é usado para especificar que um modelo de projeto é usado para criar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.

## <a name="syntax"></a>Sintaxe

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Especifica a versão do sistema operacional que o modelo de projeto tem como destino.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

## <a name="remarks"></a>Comentários
 O texto deve ser **Windows**.

## <a name="example"></a>Exemplo
 Este exemplo especifica que o modelo de projeto tem como destino [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou posterior.

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Confira também
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

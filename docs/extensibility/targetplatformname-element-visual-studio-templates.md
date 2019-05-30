---
title: Elemento TargetPlatformName (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c307a52b8f252f5059f2d4009e98fc4d497f616e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316705"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>Elemento TargetPlatformName (Modelos do Visual Studio)
Especifica a plataforma de que os destinos de modelo de projeto. Esse elemento é usado para especificar que um modelo de projeto é usado para criar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.

## <a name="syntax"></a>Sintaxe

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Especifica a versão do sistema operacional que os destinos de modelo de projeto.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

## <a name="remarks"></a>Comentários
 O texto deve ser **Windows**.

## <a name="example"></a>Exemplo
 Este exemplo especifica que os destinos de modelo de projeto [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou posterior.

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Consulte também
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
---
title: RequiredPlatformVersion Element (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701492"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (modelos do Visual Studio)
Especifica a versão mínima do sistema operacional que o modelo de projeto requer para funcionar corretamente. Este elemento é usado para modelos de projeto que criam [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos.

 O `RequiredPlatformVersion` valor é comparado diretamente com a versão do sistema operacional. Se `RequiredPlatformVersion` o for maior do que a versão do sistema operacional, o modelo não aparecerá na caixa de diálogo **Novo Projeto.** Para especificar [!INCLUDE[win8](../debugger/includes/win8_md.md)] um modelo `RequiredPlatformVersion` para ou superior, defina como 6.2.0. Para especificar [!INCLUDE[win81](../debugger/includes/win81_md.md)] um modelo `RequiredPlatformVersion` para ou superior, defina como 6.3.0.

 Modelos que `RequiredPlatformVersion`especificam =8 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] são compatíveis com modelos de clienteanteriores.

 VSTemplate Data-modelo ..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Sintaxe

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 Nenhum.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplatePlatformNome](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica a plataforma que o modelo de projeto tem como alvo.|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

## <a name="remarks"></a>Comentários
 Este texto especifica a versão mínima do sistema operacional exigida pelo modelo.

## <a name="example"></a>Exemplo
 Este exemplo especifica que o [!INCLUDE[win8](../debugger/includes/win8_md.md)] modelo de projeto tem como alvo ou posterior.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Confira também
- [Elemento TargetPlatformName (modelos do Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

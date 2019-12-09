---
title: Registrando modelos de projeto e item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724621"
---
# <a name="registering-project-and-item-templates"></a>Registrando modelos de projeto e item
Os tipos de projeto devem registrar os diretórios em que os modelos de projeto e de item de projeto estão localizados. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa as informações de registro associadas aos tipos de projeto para determinar o que mostrar nas caixas de diálogo **Adicionar novo projeto** e **Adicionar novo item** .

 Para obter mais informações sobre modelos, consulte [adicionando projeto e modelos de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Entradas de registro para projetos
 Os exemplos a seguir mostram entradas de registro em HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*versão*>. As tabelas que as acompanham explicam os elementos usados nos exemplos.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Name|Digite|Descrição|
|----------|----------|-----------------|
|@|REG_SZ|Nome padrão dos projetos deste tipo.|
|DisplayName|REG_SZ|ID de recurso do nome a ser recuperado da DLL satélite registrada em pacotes.|
|Pacote|REG_SZ|ID de classe do pacote registrado em pacotes.|
|ProjectTemplatesDir|REG_SZ|Caminho padrão dos arquivos de modelo de projeto. Os arquivos de modelo de projeto são exibidos pelo novo modelo de **projeto** .|

### <a name="registering-item-templates"></a>Registrando modelos de item
 Você deve registrar o diretório onde você armazena os modelos de item.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Name | Digite | Descrição |
|--------------------------|-----------| - |
| @ | REG_SZ | ID do recurso para adicionar modelos de item. |
| TemplatesDir | REG_SZ | Caminho dos itens de projeto exibidos na caixa de diálogo para o assistente **Adicionar novo item** . |
| TemplatesLocalizedSubDir | REG_SZ | ID de recurso de uma cadeia de caracteres que nomeia o subdiretório de TemplatesDir que contém modelos localizados. Como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o recurso de cadeia de caracteres de DLLs satélite, se você os tiver, cada DLL satélite poderá conter um nome de subdiretório localizado diferente. |
| SortPriority | REG_DWORD | Defina SortPriority para controlar a ordem na qual os modelos são exibidos na caixa de diálogo **Adicionar novo item** . Valores SortPriority maiores aparecem anteriormente na lista de modelos. |

### <a name="registering-file-filters"></a>Registrando filtros de arquivo
 Opcionalmente, você pode registrar filtros que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa quando ele solicita nomes de arquivo. Por exemplo, o filtro de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] para a caixa de diálogo **Abrir arquivo** é:

 **Arquivos C# visuais (\*. cs, \*. resx, \*. settings, \*. xsd, \*. WSDL); \*. cs, \*. resx, \*. Settings, 0. xsd, 1. WSDL)**

 Para dar suporte ao registro de vários filtros, cada filtro é registrado em sua própria subchave em HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ <*versão*> \projects \\ {\<*ProjectGuid*>} \Filters >*subchave*de < \\. O nome da subchave é arbitrário;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora o nome da subchave e usa apenas seus valores.

 Você pode controlar os contextos nos quais um filtro é usado definindo sinalizadores, mostrados na tabela a seguir. Se um filtro não tiver nenhum sinalizador definido, ele será listado após os filtros comuns na caixa de diálogo **Adicionar item existente** e na caixa de diálogo **Abrir arquivo** , mas não será usado na caixa de diálogo **localizar nos arquivos** .

```
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]
@="#3"
"CommonOpenFilesFilter"=dword:00000000
"CommonFindFilesFilter"=dword:00000000
"FindInFilesFilter"=dword:00000000
"NotOpenFileFilter"=dword:00000000
"NotAddExistingItemFilter"=dword:00000000
"SortPriority"=dword:00000064
```

|Name|Digite|Descrição|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Torna o filtro um dos filtros comuns na caixa de diálogo **localizar nos arquivos** . Os filtros comuns são listados na lista filtro antes dos filtros não marcados como comuns.|
|CommonOpenFilesFilter|REG_DWORD|Torna o filtro um dos filtros comuns na caixa de diálogo **Abrir arquivo** . Os filtros comuns são listados na lista filtro antes dos filtros não marcados como comuns.|
|FindInFilesFilter|REG_DWORD|Lista o filtro após os filtros comuns na caixa de diálogo **localizar nos arquivos** .|
|NotOpenFileFilter|REG_DWORD|Indica que o filtro não é usado na caixa de diálogo **Abrir arquivo** .|
|NotAddExistingItemFilter|REG_DWORD|Indica que o filtro não é usado na caixa de diálogo **Adicionar item existente** .|
|SortPriority|REG_DWORD|Defina SortPriority para controlar a ordem na qual os filtros são exibidos. Valores SortPriority maiores aparecem anteriormente na lista de filtros.|

## <a name="directory-structure"></a>Estrutura de diretórios
 O VSPackages pode colocar arquivos de modelo e pastas em qualquer lugar em um disco local ou remoto, desde que o local seja registrado por meio do IDE (ambiente de desenvolvimento integrado). No entanto, para facilitar a organização, recomendamos a seguinte estrutura de diretório no caminho de instalação do seu produto.

 \Templates

 \Projects (contém os modelos de projeto)

 \Applications

 \Components

 \ ...

 \ProjectItems (contém os itens de projeto)

 \Class

 \Form

 Página \Servidor

 \HelperFiles (contém os arquivos usados em itens de projeto de vários arquivos)

 \WizardFiles

## <a name="see-also"></a>Consulte também

- [Adicionar modelos projeto e de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistentes:](../../extensibility/internals/wizards.md)
- [Localizando aplicativos](../../ide/globalizing-and-localizing-applications.md)
- [CATIDs para objetos normalmente usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
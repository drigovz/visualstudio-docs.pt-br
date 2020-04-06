---
title: Cadastrar modelos de projeto e itens | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705817"
---
# <a name="registering-project-and-item-templates"></a>Registrando modelos de projeto e item
Os tipos de projeto devem registrar os diretórios onde seus modelos de projeto e itens de projeto estão localizados. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa as informações de registro associadas aos seus tipos de projeto para determinar o que mostrar no **Adicionar novo projeto** e adicionar caixas de diálogo de novo **item.**

 Para obter mais informações sobre modelos, consulte [Adicionar modelos de projeto e itens de projeto.](../../extensibility/internals/adding-project-and-project-item-templates.md)

## <a name="registry-entries-for-projects"></a>Inscrições de Registro para Projetos
 Os exemplos a seguir mostram entradas de registro\\<em HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio*Versão*>. As tabelas que acompanham explicam os elementos utilizados nos exemplos.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Nome|Type|Descrição|
|----------|----------|-----------------|
|@|REG_SZ|Nome padrão de projetos desse tipo.|
|DisplayName|REG_SZ|ID de recursos do nome a ser recuperado do satélite DLL registrado em Pacotes.|
|Pacote|REG_SZ|ID de classe do pacote registrado em Pacotes.|
|ProjectTemplatesDir|REG_SZ|Caminho padrão dos arquivos Modelo de projeto. Os arquivos Project Template são exibidos pelo modelo **Novo Projeto.**|

### <a name="registering-item-templates"></a>Registrando modelos de itens
 Você deve registrar o diretório onde armazena modelos de itens.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nome | Type | Descrição |
|--------------------------|-----------| - |
| @ | REG_SZ | ID de recursos para adicionar modelos de itens. |
| ModelosDir | REG_SZ | Caminho dos itens do projeto exibidos na caixa de diálogo para o **assistente Adicionar novo item.** |
| ModelosLocalizadosSubDir | REG_SZ | ID de recurso de uma string que nomeia o subdiretório de TemplatesDir que contém modelos localizados. Como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o recurso de string de DLLs de satélite se você os tiver, cada DLL de satélite pode conter um nome de subdiretório localizado diferente. |
| ClassificarPrioridade | REG_DWORD | Defina SortPriority para governar a ordem em que os modelos são exibidos na caixa de diálogo **Adicionar novo item.** Valores maiores sortPriority aparecem mais cedo na lista de modelos. |

### <a name="registering-file-filters"></a>Registrando filtros de arquivos
 Opcionalmente, você pode registrar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] filtros que usam quando ele solicita nomes de arquivos. Por exemplo, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o filtro para a caixa de diálogo **Arquivo Aberto** é:

 **Arquivos Visuais C# (.cs,\*\*.resx,\*\*\*.settings, .xsd, .wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Para suportar o registro de vários filtros, cada filtro é registrado em sua\\<própria subchave\<sob HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio*Versão*>\Projects\\{*ProjectGUID*>}\Filtros\\<*Subchave*>. O nome da subchave é arbitrário; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignora o nome da subchave e usa apenas seus valores.

 Você pode controlar os contextos nos quais um filtro é usado definindo sinalizadores, mostrados na tabela a seguir. Se um filtro não tiver nenhum conjunto de sinalizadores, ele será listado após os filtros comuns na caixa de diálogo **Adicionar item existente** e na caixa de diálogo **Abrir arquivo,** mas não será usado na caixa de diálogo **Encontrar em Arquivos.**

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

|Nome|Type|Descrição|
|----------|----------|-----------------|
|CommonFindFilesFilterFiltro|REG_DWORD|Faz do filtro um dos filtros comuns na caixa de diálogo **Encontrar em Arquivos.** Os filtros comuns são listados na lista de filtros antes que os filtros não sejam marcados como comuns.|
|CommonOpenFilesFilter|REG_DWORD|Faz do filtro um dos filtros comuns na caixa de diálogo **Arquivo Aberto.** Os filtros comuns são listados na lista de filtros antes que os filtros não sejam marcados como comuns.|
|FindInFilesFilter|REG_DWORD|Lista o filtro após os filtros comuns na caixa de diálogo **Encontrar em Arquivos.**|
|Não'AbrirarquivoFiltro|REG_DWORD|Indica que o filtro não é usado na caixa de diálogo **Arquivo aberto.**|
|NotAddItItemFilter|REG_DWORD|Indica que o filtro não é usado na caixa de diálogo **Adicionar item existente.**|
|ClassificarPrioridade|REG_DWORD|Defina SortPriority para reger a ordem na qual os filtros são exibidos. Valores maiores sortPriority aparecem mais cedo na lista de filtros.|

## <a name="directory-structure"></a>Estrutura de diretórios
 O VSPackages pode colocar arquivos e pastas de modelo em qualquer lugar em um disco local ou remoto, desde que o local seja registrado através do ambiente de desenvolvimento integrado (IDE). No entanto, para facilitar a organização, recomendamos a seguinte estrutura de diretório sob o caminho de instalação do seu produto.

 \Modelos

 \Projetos (contém os modelos do projeto)

 \Aplicações

 \Componentes

 \ ...

 \ProjectItems (contém os itens do projeto)

 \Classe

 \Formulário

 \Página da Web

 \HelperFiles (contém os arquivos usados em itens de projeto de vários arquivos)

 \Arquivos de assistente

## <a name="see-also"></a>Confira também

- [Adicionando o projeto e os modelos de item do projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Assistentes](../../extensibility/internals/wizards.md)
- [Localizando aplicativos](../../ide/globalizing-and-localizing-applications.md)
- [CATIDs para objetos que normalmente são usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

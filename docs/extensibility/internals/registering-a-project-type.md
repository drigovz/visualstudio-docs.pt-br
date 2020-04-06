---
title: Registrando um tipo de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705877"
---
# <a name="registering-a-project-type"></a>Registrando um tipo de projeto
Ao criar um novo tipo de projeto, você [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve criar entradas de registro que permitam reconhecer e trabalhar com o seu tipo de projeto. Você normalmente cria essas entradas de registro usando um arquivo de script de registro (.rgs).

 No exemplo abaixo, as declarações do registro fornecem caminhos e dados padrão quando aplicável, seguidos de uma tabela que contém entradas do script de registro para cada declaração. As tabelas fornecem as entradas de script e informações adicionais sobre as declarações.

> [!NOTE]
> As seguintes informações de registro destinam-se a ser um exemplo do tipo e propósitos das entradas nos scripts de registro que você estará escrevendo para registrar o seu tipo de projeto. Suas entradas reais e seus usos podem variar de acordo com os requisitos específicos do seu tipo de projeto. Você deve rever as amostras disponíveis para encontrar uma que se assemelhe ao tipo de projeto que você está desenvolvendo e, em seguida, revise o script de registro dessa amostra.

 Os exemplos a seguir são de HKEY_CLASSES_ROOT.

## <a name="example"></a>Exemplo

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|Nome e descrição dos arquivos do tipo de projeto que possuem a extensão .figp.|
|`Content Type`|REG_SZ|`Text/plain`|Tipo de conteúdo para os arquivos do projeto.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|Ícone padrão usado para projeto deste tipo. A declaração %MODULE% é concluída no registro para o local padrão do dLL tipo projeto.|
|`@`|REG_SZ|`&Open in Visual Studio`|Aplicativo padrão no qual esse tipo de projeto será aberto.|
|`@`|REG_SZ|`devenv.exe "%1"`|O comando padrão será executado quando um projeto desse tipo for aberto.|

 Os exemplos a seguir são de HKEY_LOCAL_MACHINE e estão localizados no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].

## <a name="example"></a>Exemplo

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`@` (Padrão)|REG_SZ|`FigPrj Project VSPackage`|Nome localizado deste VSPackage (tipo de projeto) registrado.|
|`InprocServer32`|REG_SZ|`%MODULE%`|Caminho do projeto tipo DLL. O IDE carrega este DLL e passa `DllGetClassObject` o <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> CLSID para conseguir construir o objeto.|
|`CompanyName`|REG_SZ|`Microsoft`|Nome da empresa que desenvolveu o tipo de projeto.|
|`ProductName`|REG_SZ|`Figure Project Sample`|Nome para o tipo de projeto.|
|`ProductVersion`|REG_SZ|`9.0`|Número da versão da versão do tipo de projeto.|
|`MinEdition`|REG_SZ|`professional`|Edição do VSPackage sendo registrado.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|A chave de carga do pacote para o projeto VSPackage. A chave é validada quando um projeto é carregado após o início do ambiente.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nome do arquivo do dLL do satélite que contém recursos localizados para o tipo de projeto.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Caminho do satélite DLL.|
|`FigProjectsEvents`|REG_SZ|Veja a declaração de valor.|Determina a seqüência de texto retornada para este evento de automação.|
|`FigProjectItemsEvents`|REG_SZ|Veja a declaração de valor.|Determina a seqüência de texto retornada para este evento de automação.|

 Todos os exemplos a seguir estão localizados no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Exemplo

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|Nome padrão de projetos deste tipo.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|ID de recursos do nome a ser recuperado do satélite DLL registrado em Pacotes.|
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe do VSPackage registrado em Pacotes.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão dos arquivos do Modelo de Projeto. Estes são os arquivos exibidos pelo modelo Novo Projeto.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Caminho padrão dos arquivos do Project Item Template. Estes são os arquivos exibidos pelo modelo Adicionar novo item.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Habilita o IDE para implementar a caixa de diálogo **Abrir.**|
|`PossibleProjectExtensions`|REG_SZ|`figp`|Usado pelo IDE para determinar se o projeto que está sendo aberto é tratado por esse tipo de projeto (fábrica de projetos). O formato para mais de uma entrada é uma lista delimitada de ponto e vírgula. Por exemplo, "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|Usado pelo IDE como a extensão de nome de arquivo padrão para a operação Salvar como.|
|`Filter Settings`|REG_DWORD|Vários, veja declarações e comentários seguindo a tabela.|Essas configurações são usadas para definir os vários filtros para exibir arquivos em caixas de diálogo uI.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID de recursos para adicionar modelos de itens.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Caminho dos itens do projeto exibidos na caixa de diálogo para o modelo **Adicionar novo item.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Determina a ordem de classificação no nó de árvore dos arquivos exibidos na caixa de diálogo **Adicionar novo item.**|

 A tabela a seguir mostra as opções Filtros disponíveis no segmento de código anterior.

|Opção de filtro|Descrição|
|-------------------|-----------------|
|`CommonFindFilesFilter`|Indica que o filtro é um dos filtros comuns na caixa de diálogo **Encontrar em Arquivos.** Os filtros comuns estão listados na lista de filtros antes que os filtros não sejam marcados como comuns.|
|`CommonOpenFilesFilter`|Indica que o filtro é um dos filtros comuns na caixa de diálogo **Arquivo Aberto.** Os filtros comuns estão listados na lista de filtros antes que os filtros não sejam marcados como comuns.|
|`FindInFilesFilter`|Indica que o filtro será um dos filtros na caixa de diálogo **Encontrar em Arquivos** e será listado após os filtros comuns.|
|`NotOpenFileFilter`|Indica que o filtro não será usado na caixa de diálogo **Arquivo Aberto.**|
|`NotAddExistingItemFilter`|Indica que o filtro não será usado na caixa de diálogo Adicionar **item existente.**|

 Por padrão, se um filtro não tiver um ou mais desses sinalizadores definidos, o filtro será usado na caixa de diálogo **Adicionar item existente** e na caixa de diálogo **Abrir arquivo** após a lista de filtros comuns. O filtro não é usado na caixa de diálogo **Encontrar em Arquivos.**

 Todos os exemplos a seguir estão localizados no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Exemplo

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID de recursos para novos modelos de projeto.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão para projetos do tipo de projeto cadastrado.|
|`SortPriority`|REG_DWORD|`41 (x29)`|Define a ordem de tipos de projetos exibidos na caixa de diálogo assistente de Novos projetos.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que projetos deste tipo são exibidos apenas na caixa de diálogo Projeto Novo.|

 Todos os exemplos a seguir estão localizados no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].

## <a name="example"></a>Exemplo

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|Nenhum|Valor padrão que indica que as seguintes entradas são para as entradas de projetos Arquivos Diversos.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valor de ID de recurso para adicionar arquivos de modelo de novos itens.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Caminho padrão dos itens que serão exibidos na caixa de diálogo **Adicionar novo item.**|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Estabelece ordem de classificação para exibição no nó de árvore da caixa de diálogo **Adicionar novo item.**|

 O exemplo a seguir está localizado no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].

## <a name="example"></a>Exemplo

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 A entrada do menu aponta o IDE para o recurso usado para recuperar as informações do menu. Quando esses dados forem mesclados no banco de dados do menu, a mesma chave será adicionada na seção MenusMerged do registro. O VSPackage não deve modificar nada na seção MenusMerged diretamente. No campo Data na tabela a seguir, há três campos separados por comma. O primeiro campo identifica um caminho completo de um arquivo de recurso de menu:

- Se o primeiro campo for omitido, o recurso de menu será carregado a partir do dLL do satélite identificado pelo VSPackage GUID.

  O segundo campo identifica um ID de recurso de menu do tipo CTMENU:

- Se o ID de recurso for especificado e o caminho do arquivo for fornecido pelo primeiro parâmetro, um recurso de menu será carregado a partir do caminho completo do arquivo.

- Se o ID de recurso for fornecido, mas o caminho do arquivo não for, o recurso do menu será carregado a partir do DLL do satélite.

- Se o caminho completo do arquivo for fornecido e o ID de recurso for omitido, espera-se que o arquivo a ser carregado seja um arquivo CTO.

  O último campo identifica o número da versão para o recurso CTMENU. Você pode mesclar o menu novamente alterando o número da versão.

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|O recurso para recuperar as informações do menu.|

 Todos os exemplos a seguir estão localizados no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Valor de ID de recursos para os modelos do Projeto Figures New Project.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Caminho padrão do diretório Novos Projetos. Os itens deste diretório serão exibidos na caixa de diálogo assistente do **Novo Projeto.**|
|`SortPriority`|REG_DWORD|`41 (x29)`|Estabelece a ordem em que os projetos serão exibidos no nó de árvore da caixa de diálogo **Projeto Novo.**|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 indica que projetos deste tipo são exibidos apenas na caixa de diálogo **Projeto Novo.**|

 O exemplo a seguir está localizado no registro sob a chave [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|Nome|Type|Dados|Descrição|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|ID de classe do VSPackage registrado.|
|`UseInterface`|REG_DWORD|`1`|1 indica que a ui será usada para interagir com este projeto. 0 indica que não há interface de interface de interface.|

 Os arquivos.vsz que controlam novos tipos de projeto frequentemente contêm uma entrada RELATIVE_PATH. Este caminho é relativo ao caminho especificado em \ProductDir entrada do tipo de projeto na seguinte tecla Configuração:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Configuração

 Por exemplo, os modelos de projeto Enterprise Frameworks adicionam as seguintes entradas de registro:

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Arquivos de programa\Microsoft Visual Studio\EnterpriseFrameworks\

 Isso significa que se você incluir uma entrada PROJECT_TYPE=EF no arquivo .vsz, o ambiente encontra seus arquivos .vsz no diretório ProductDir especificado anteriormente.

## <a name="see-also"></a>Confira também
- [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)
- [Criando instâncias de projeto por meio de fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

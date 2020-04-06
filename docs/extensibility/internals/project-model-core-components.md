---
title: Componentes do Núcleo do Modelo do Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706531"
---
# <a name="project-model-core-components"></a>Componentes principais do projeto modelo
As tabelas a seguir se expandem no modelo do projeto. As tabelas apresentam breves descrições das interfaces e serviços identificados no modelo e das interfaces e serviços associados a objetos específicos. Além disso, as tabelas detalham outras interfaces que são opcionais na criação e manutenção do projeto, dependendo dos requisitos do seu tipo de projeto específico.

 Para obter mais informações, consulte [Como suporte às ferramentas de navegação por símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objeto de pacote

|Interface|Comentários|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicia um VSPackage no IDE e disponibiliza seus serviços para o IDE.|

### <a name="project-factory-object"></a>Objeto project factory

|Interface|Comentários|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gerencia a criação de novos projetos e a abertura de projetos existentes.|

### <a name="project-objects"></a>Objetos de projeto

|Interfaces|Comentários|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gerencia a adição e remoção de itens do projeto, abre editores `VSITEMID`e mantém o mapeamento entre cada apelido de documento e o . Herda `IVsProject` e. `IVsProject2`|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gerencia propriedades de navegação e exibição e fornece eventos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita a execução `IOleCommandTarget` de comandos semelhante à de comandos como Cut e Rename que se aplicam apenas quando o foco está no Solution Explorer.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Serve como a interface de destino de comando principal para uma hierarquia de projeto. É a interface padrão para consultar objetos para seu status de comando ou estado e executar comandos. Disponível quando você não estiver focado na janela Do Projeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordena a persistência do estado do projeto. Normalmente, o estado do projeto é armazenado como um arquivo de projeto, mas pode ser adaptado a sistemas de armazenamento que não são baseados em arquivos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite que o projeto gerencie todos os aspectos de persistência para seus itens de projeto, seja como arquivos em disco ou objetos em outros sistemas de armazenamento. A `IVsPersistHierarchyItem2` interface é usada para itens que <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> não implementam a interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordena interações com controle de código fonte.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite que os projetos gerenciem informações de configuração.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gerencia objetos de configuração de projeto, como configurações Debug/Release. As operações de construção, implantação e depuração são coordenadas através de objetos de configuração do projeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por hierarquias para controlar as opções de exclusão (destrutiva) ou remover (não destrutivas) para itens de hierarquia. Chamada Interface de `IVsHierarchyDeleteHandler` consulta na `IVsHierarchy` interface da interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornece a opção de implementação de `IVsCfgProvider2` ter o objeto que suporta a interface `IVsHierarchy` em uma identidade COM diferente do objeto de projeto que implementa a interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interface opcional implementada para tornar seu projeto extensível por outros desenvolvedores. A `IVsProjectStartupServices` interface permite que um VSPackage de terceiros registre um GUID que você persiste em seu arquivo de projeto para que `QueryService` cada vez que seu projeto seja carregado, você carregue o GUID de serviço de terceiros no seu arquivo de projeto e peça esse GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado pelas hierarquias `UIHierarchy` de origem em uma janela para coordenar operações de área de transferência, como corte, cópia e colar. Use `AdviseClipboardHelperEvents` a interface para registrar eventos de área de transferência.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornece informações sobre um item arrastado em relação à sua fonte de dados durante uma operação de arrastar e soltar em uma janela de hierarquia de UI. Chamado da `IVsHierarchy` interface.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornece informações sobre um item arrastado em relação ao seu alvo de queda durante uma operação de arrastar e soltar em uma janela de hierarquia de UI. Chamado da `IVsHierarchy` interface.|

### <a name="configuration-object"></a>Objeto de configuração

|Interfaces|Comentários|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornece informações sobre uma configuração.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite que os projetos gerenciem informações de configuração.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite que um projeto seja executado sob o controle do depurador.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por projetos de implantação que executam operações de implantação para outros projetos.|

### <a name="configuration-builder-object"></a>Objeto do Construtor de Configuração

|Interfaces|Comentários|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gerencia a operação de compilação de uma configuração de projeto.|

### <a name="additional-project-objects"></a>Objetos adicionais do Projeto

|Interfaces|Comentários|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Exibe propriedades do item na janela **Propriedades.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Exibe saídas para implantação.|

 A tabela a seguir apresenta breves descrições dos serviços identificados no modelo do projeto.

### <a name="services"></a>Serviços

|Serviço|Comentários|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usado por VSPackages que implementam tipos de projetos para registrar que sua fábrica de projetos existe com o IDE. Seu VSPackage `QueryService` deve chamar este serviço e `IVsPackage::SetSite` registrar sua fábrica de projetos quando o método é chamado. Se `SetSite` o método não for chamado, seu projeto não será instanciado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornece acesso à noção interna e incorporada do IDE da solução atual, como a capacidade de enumerar projetos, criar novos projetos, tomar conhecimento das mudanças de projeto, e assim por diante.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chamado por projetos que desejam participar do controle de fontes.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantém uma tabela de documentos abertos para determinar se um ou mais itens do projeto já estão abertos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contém as interfaces e métodos chamados para realmente abrir um item de projeto usando o editor padrão ou um editor específico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Necessário para ser chamado por todos os projetos quando eles adicionam, removem ou renomeiam seus itens.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gerencia alterações em um arquivo ou diretório e notifica os clientes quando os arquivos selecionados foram alterados no disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Necessário para ser chamado por todos os projetos e editores antes que eles subecem itens ou salvá-los.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Gerencia a ordem das operações de construção e implantação para configurações do projeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornece acesso a serviços de depuração de baixo nível usados para a maioria dos controles de depuração.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita o VSPackages acesso a informações sobre seleções atuais e permite a comunicação com a janela **Propriedades.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornece funcionalidade básica de IDE relacionada à UI, como a capacidade de criar e enumerar janelas de ferramentas ou janelas de documentos ou relatar um erro ao usuário.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Fornece acesso à barra de status do IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Usado para implementar o modelo de automação. No modelo do projeto, você devolverá um objeto de propriedades que permite criar uma instância desse objeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Usado para implementar eventos de área de transferência no objeto do projeto na hierarquia. `SVsUIHierWinClipboardHelper`permite que você manuseie corretamente as operações de corte, cópia e cola.|

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Não em construção: usando classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)

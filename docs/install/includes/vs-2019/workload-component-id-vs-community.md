---
title: IDs de carga de trabalho e de componente do Visual Studio Community 2019
titleSuffix: ''
description: Use as IDs de carga de trabalho e de componente para instalar o Visual Studio usando a linha de comando ou para especificar como uma dependência em um manifesto do VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 03/01/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 61b5a7e251f4c20a2118869605b89b0cea21ffc3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160943"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2019"></a>Editor principal do Visual Studio (incluído no Visual Studio Community 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descrição:** A experiência do shell do núcleo do Visual Studio, incluindo edição de código com reconhecimento de sintaxe, controle do código-fonte e gerenciamento de itens de trabalho.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor do Visual Studio Core | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Página inicial do Visual Studio para usuários C++ | 16.0.28315.86 | Opcional

## <a name="azure-development"></a>Desenvolvimento do Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrição:** SDKs do Azure, ferramentas e projetos para desenvolver aplicativos na nuvem, criar recursos e criar Contêineres, incluindo o suporte ao Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Necessária
Component.Microsoft.VisualStudio.Web.AzureFunctions | Ferramentas do Azure WebJobs | 16.0.28625.61 | Necessária
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Necessária
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28516.191 | Necessária
Microsoft.NetCore.ComponentGroup.Web.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Suporte à linguagem F# para projetos Web | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Pré-requisitos de desenvolvimento do Azure | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Ferramentas do Azure WebJobs | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.Component.Azure.DataLake.Tools | Ferramentas Azure Data Lake e Stream Analytics | 16.0.28625.61 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 16.0.28517.75 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 16.0.28516.191 | Recomendado
Microsoft.VisualStudio.Component.AspNet45 | Recursos avançados do ASP.NET | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Ferramentas do Visual Studio para Kubernetes | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Principais ferramentas do Azure Resource Manager | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Ferramentas do Service Fabric | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Ferramentas de build dos Serviços de Nuvem do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Ferramentas dos Serviços de Nuvem do Azure | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Ferramentas do Azure Resource Manager | 16.0.28528.71 | Recomendado
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 16.0.28621.142 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7.1 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 16.0.28516.191 | Opcional
Microsoft.Net.Core.Component.SDK.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28516.191 | Opcional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy do Armazenamento do Azure | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Opcional

## <a name="data-storage-and-processing"></a>Armazenamento de dados e processamento

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrição:** Conecte-se, desenvolva e teste as soluções de dados com o SQL Server, o Azure Data Lake ou o Hadoop.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Recomendado
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Recomendado
Microsoft.Component.Azure.DataLake.Tools | Ferramentas Azure Data Lake e Stream Analytics | 16.0.28625.61 | Recomendado
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 16.0.28517.75 | Recomendado
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 16.0.28516.191 | Recomendado
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Recomendado
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Ferramentas de build dos Serviços de Nuvem do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Recomendado
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Recomendado
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.FSharp.Desktop | Suporte à linguagem F# da área de trabalho | 16.0.28315.86 | Opcional

## <a name="data-science-and-analytical-applications"></a>Ciência de dados e aplicativos analíticos

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descrição:** Linguagens e ferramentas para criação de aplicativos de ciência de dados, incluindo Python e F#.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.PythonTools | Suporte da linguagem Python | 16.0.28625.61 | Recomendado
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.0.28625.61 | Recomendado
Microsoft.Component.PythonTools.Web | Suporte Web do Python | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.FSharp.Desktop | Suporte à linguagem F# da área de trabalho | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Recomendado
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Recomendado
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 16.0.28625.61 | Opcional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Ferramentas de desenvolvimento nativo do Python | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – ferramentas de build do C++ para VS 2015 (v14.00) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK do Windows 10 (10.0.17763.0) | 16.0.28517.75 | Opcional

## <a name="net-desktop-development"></a>Desenvolvimento de área de trabalho do .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrição:** Crie aplicativos WPF, Windows Forms e de console usando C#, Visual Basic e F#.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Ferramentas de desenvolvimento de área de trabalho do .NET | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Necessária
Component.Microsoft.VisualStudio.LiveShare | Live Share – Versão Prévia | 0.3.1225.0 | Recomendado
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 16.0.28517.75 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 16.0.28516.191 | Recomendado
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.EntityFramework | Ferramentas do Entity Framework 6 | 16.0.28315.86 | Recomendado
Component.Dotfuscator | Proteção PreEmptive – Dotfuscator | 16.0.28528.71 | Opcional
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Opcional
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 16.0.28621.142 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7.1 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 16.0.28516.191 | Opcional
Microsoft.Net.Core.Component.SDK.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28516.191 | Opcional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28516.191 | Opcional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.FSharp.Desktop | Suporte à linguagem F# da área de trabalho | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.PortableLibrary | Pacote de direcionamento da Biblioteca Portátil do .NET | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Opcional

## <a name="game-development-with-unity"></a>Desenvolvimento de jogos com Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrição:** Crie jogos 2D e 3D com o Unity, um ambiente de desenvolvimento multiplataforma avançado.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 3.5 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.1 | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Unity | Ferramentas do Visual Studio para Unity | 16.0.28315.86 | Necessária
Component.UnityEngine.x64 | Editor de 64 bits do Unity 2018.3 | 16.0.28528.71 | Recomendado
Component.UnityEngine.x86 | Editor de 32 bits do Unity 5.6 | 16.0.28315.86 | Recomendado

## <a name="linux-development-with-c"></a>Desenvolvimento de Linux com C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrição:** Crie e depure aplicativos executados em um ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.MDD.Linux | Desenvolvimento do C++ para Linux | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 16.0.28315.86 | Necessária
Component.Linux.CMake | Ferramentas CMake do C++ para Linux | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK do Windows 10 (10.0.17763.0) | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Recomendado
Component.MDD.Linux.GCC.arm | Ferramentas de desenvolvimento inseridas e de IoT | 16.0.28625.61 | Opcional

## <a name="desktop-development-with-c"></a>Desenvolvimento de área de trabalho com o C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrição:** Crie aplicativos da área de trabalho do Windows usando o conjunto de ferramentas Microsoft C++, o ATL ou o MFC.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Atualização dos Pacotes Redistribuíveis do C++ 2019 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Principais recursos de área de trabalho do Visual C++ | 16.0.28315.86 | Necessária
Component.Microsoft.VisualStudio.LiveShare | Live Share – Versão Prévia | 0.3.1225.0 | Recomendado
Microsoft.VisualStudio.Component.Debugger.JustInTime | Depurador Just-In-Time | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.VC.ATL | ATL do C++ para ferramentas de build v142 (x86 e x64) | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.VC.CMake.Project | Ferramentas CMake do C++ para Windows | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adaptador de Teste para Boost.Test | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Adaptador de Teste para Google Test | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK do Windows 10 (10.0.17763.0) | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Recomendado
Component.Incredibuild | IncrediBuild - Aceleração de Build | 16.0.28528.71 | Opcional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Opcional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 16.0.28625.61 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – ferramentas de build do C++ para VS 2015 (v14.00) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC do C++ para ferramentas de build v142 (x86 e x64) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.CLI.Support | Suporte do C++/CLI para ferramentas de build v142 | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos do C++ para ferramentas de build v142 (x64/x86 – experimental) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – ferramentas de build do C++ para VS 2017 x64/x86 (v14.16) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK do Windows 10 (10.0.16299.0) | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK do Windows 10 (10.0.17134.0) | 16.0.28517.75 | Opcional

## <a name="game-development-with-c"></a>Desenvolvimento de jogos com C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrição:** Use todo o poder do C++ para criar jogos profissionais da plataforma DirectX, Unreal ou Cocos2d.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Atualização dos Pacotes Redistribuíveis do C++ 2019 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK do Windows 10 (10.0.17763.0) | 16.0.28517.75 | Recomendado
Component.Android.NDK.R16B | NDK do Android (R16B) | 16.0.28625.61 | Opcional
Component.Android.SDK25.Private | Instalação do SDK do Android (nível da API 25) (instalação local para Desenvolvimento Móvel com C++) | 16.0.28625.61 | Opcional
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Opcional
Component.Cocos | Cocos | 16.0.28315.86 | Opcional
Component.Incredibuild | IncrediBuild - Aceleração de Build | 16.0.28528.71 | Opcional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Opcional
Component.MDD.Android | Ferramentas de desenvolvimento do Android para C++ | 16.0.28517.75 | Opcional
Component.OpenJDK | OpenJDK (distribuição da Microsoft) | 16.0.28625.61 | Opcional
Component.Unreal | Instalador do Unreal Engine | 16.0.28625.61 | Opcional
Component.Unreal.Android | Suporte do IDE do Android para Unreal Engine | 16.0.28625.61 | Opcional
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 16.0.28517.75 | Opcional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 16.0.28516.191 | Opcional
Microsoft.VisualStudio.Component.NuGet.BuildTools | Os destinos e as tarefas de compilação do NuGet | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Opcional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK do Windows 10 (10.0.16299.0) | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK do Windows 10 (10.0.17134.0) | 16.0.28517.75 | Opcional

## <a name="mobile-development-with-c"></a>Desenvolvimento móvel com C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrição:** Crie aplicativos multiplataforma para iOS, Android ou Windows usando o C++.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Android.SDK25.Private | Instalação do SDK do Android (nível da API 25) (instalação local para Desenvolvimento Móvel com C++) | 16.0.28625.61 | Necessária
Component.OpenJDK | OpenJDK (distribuição da Microsoft) | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Necessária
Component.Android.NDK.R16B | NDK do Android (R16B) | 16.0.28625.61 | Recomendado
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Recomendado
Component.MDD.Android | Ferramentas de desenvolvimento do Android para C++ | 16.0.28517.75 | Recomendado
Component.Android.NDK.R16B_3264 | NDK do Android (R16B) (32 bits) | 16.0.28625.61 | Opcional
Component.Google.Android.Emulator.API25.Private | Google Android Emulator (Nível da API 25) (instalação local) | 16.0.28625.61 | Opcional
Component.HAXM.Private | Intel HAXM (Hardware Accelerated Execution Manager) (instalação local) | 16.0.28528.71 | Opcional
Component.Incredibuild | IncrediBuild - Aceleração de Build | 16.0.28528.71 | Opcional
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | Opcional
Component.MDD.IOS | Ferramentas de desenvolvimento do iOS para C++ | 16.0.28517.75 | Opcional

## <a name="net-core-cross-platform-development"></a>Desenvolvimento de plataforma cruzada do .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrição:** Crie aplicativos multiplataforma usando .NET Core, ASP.NET Core, HTML/JavaScript e Contêineres, incluindo o suporte ao Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Necessária
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Necessária
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28516.191 | Necessária
Microsoft.NetCore.ComponentGroup.Web.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Suporte à linguagem F# para projetos Web | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Component.Microsoft.VisualStudio.LiveShare | Live Share – Versão Prévia | 0.3.1225.0 | Recomendado
Component.Microsoft.VisualStudio.Web.AzureFunctions | Ferramentas do Azure WebJobs | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Ferramentas do Azure WebJobs | 16.0.28621.142 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Ferramentas de nuvem de desenvolvimento para a Web | 16.0.28621.142 | Recomendado
Microsoft.Net.Core.Component.SDK.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28516.191 | Opcional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Suporte ao IIS no tempo de desenvolvimento | 16.0.28315.86 | Opcional

## <a name="mobile-development-with-net"></a>Desenvolvimento móvel com o .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrição:** Crie aplicativos multiplataforma para iOS, Android ou Windows usando o Xamarin.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Xamarin | Xamarin | 16.0.28625.61 | Necessária
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Necessária
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28516.191 | Necessária
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.Merq | Ferramentas internas comuns do Xamarin | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.MonoDebugger | Depurador mono | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Mecanismo de modelagem ASP.NET | 16.0.28315.86 | Necessária
Component.Android.SDK27 | Instalação do SDK do Android (nível 27 da API) | 16.0.28517.75 | Recomendado
Component.OpenJDK | OpenJDK (distribuição da Microsoft) | 16.0.28625.61 | Recomendado

## <a name="aspnet-and-web-development"></a>Desenvolvimento do ASP.NET e para a Web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrição:** Crie aplicativos Web usando ASP.NET, ASP.NET Core, HTML/JavaScript e Contêineres, incluindo o suporte ao Docker.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Necessária
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Necessária
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28516.191 | Necessária
Microsoft.NetCore.ComponentGroup.Web.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.FSharp | Suporte à linguagem F# | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Suporte à linguagem F# para projetos Web | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Component.Microsoft.VisualStudio.LiveShare | Live Share – Versão Prévia | 0.3.1225.0 | Recomendado
Component.Microsoft.VisualStudio.Web.AzureFunctions | Ferramentas do Azure WebJobs | 16.0.28625.61 | Recomendado
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 16.0.28517.75 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 16.0.28516.191 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.AspNet45 | Recursos avançados do ASP.NET | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.EntityFramework | Ferramentas do Entity Framework 6 | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Ferramentas do Azure WebJobs | 16.0.28621.142 | Recomendado
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Ferramentas de nuvem de desenvolvimento para a Web | 16.0.28621.142 | Recomendado
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 16.0.28621.142 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7.1 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 16.0.28516.191 | Opcional
Microsoft.Net.Core.Component.SDK.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28516.191 | Opcional
Microsoft.NetCore.ComponentGroup.Web.2.2 | Ferramentas de desenvolvimento do .NET Core 2.2 | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Modelos de projeto adicionais (versões anteriores) | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Suporte ao IIS no tempo de desenvolvimento | 16.0.28315.86 | Opcional

## <a name="nodejs-development"></a>Desenvolvimento do Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrição:** Crie aplicativos de rede escalonáveis usando o Node.js, um tempo de execução do JavaScript controlado por eventos assíncronos. 

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Node.Tools | Ferramentas de desenvolvimento em Node.js | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Component.Microsoft.VisualStudio.LiveShare | Live Share – Versão Prévia | 0.3.1225.0 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Opcional

## <a name="officesharepoint-development"></a>Desenvolvimento para Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrição:** Crie suplementos do Office e do SharePoint, soluções do SharePoint e suplementos do VSTO usando C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Necessária
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Necessária
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Ferramentas de desenvolvimento de área de trabalho do .NET | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools para Visual Studio | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.TeamOffice | VSTO (Visual Studio Tools para Office) | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.1 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 16.0.28517.75 | Opcional
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 16.0.28621.142 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7.1 | 16.0.28516.191 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 16.0.28516.191 | Opcional
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Opcional

## <a name="python-development"></a>Desenvolvimento do Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descrição:** Edição, depuração, desenvolvimento interativo e controle do código-fonte para Python.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.PythonTools | Suporte da linguagem Python | 16.0.28625.61 | Necessária
Component.CPython3.x64 | Python 3 de 64 bits (3.7.2) | 3.7.2 | Recomendado
Component.Microsoft.VisualStudio.LiveShare | Live Share – Versão Prévia | 0.3.1225.0 | Recomendado
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.0.28625.61 | Recomendado
Microsoft.Component.PythonTools.Web | Suporte Web do Python | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.Component.Common.Azure.Tools | Ferramentas de conectividade e publicação | 16.0.28315.86 | Recomendado
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.WebDeploy | Implantação da Web | 16.0.28517.75 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Recomendado
Component.CPython2.x64 | Python 2 de 64 bits (2.7.15) | 2.7.15 | Opcional
Component.CPython2.x86 | Python 2 de 32 bits (2.7.15) | 2.7.15 | Opcional
Component.CPython3.x86 | Python 3 de 32 bits (3.7.2) | 3.7.2 | Opcional
Component.Microsoft.VisualStudio.RazorExtension | Razor Language Services | 16.0.28315.86 | Opcional
Component.Microsoft.Web.LibraryManager | Gerenciador de Biblioteca | 16.0.28315.86 | Opcional
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Opcional
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 16.0.28625.61 | Opcional
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Ferramentas de desenvolvimento nativo do Python | 16.0.28621.142 | Opcional
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Opcional
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Opcional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Opcional
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Ferramentas de Criação do Azure | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Azure.ClientLibs | Bibliotecas do Azure para .NET | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulador de Computação do Azure | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulador de Armazenamento do Azure | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Azure.Waverton | Principais ferramentas dos Serviços de Nuvem do Azure | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Ferramentas de build dos Serviços de Nuvem do Azure | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.DockerTools | Ferramentas de desenvolvimento de contêiner | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Núcleo da carga de trabalho de área de trabalho gerenciada | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC do SQL Server | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | Utilitários de linha de comando do SQL Server | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Opcional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.SQL.ADAL | Tempo de execução do SQL ADAL | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.SQL.DataSources | Fontes de dados para suporte do SQL Server | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.SQL.SSDT | Ferramentas de dados do SQL Server | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 – ferramentas de build do C++ para VS 2015 (v14.00) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Ferramentas de criação de perfil do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Web | Ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK do Windows 10 (10.0.17763.0) | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.ComponentGroup.Web | Pré-requisitos de ferramentas de desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Opcional

## <a name="universal-windows-platform-development"></a>Desenvolvimento na Plataforma Universal do Windows

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrição:** Crie aplicativos para a Plataforma Universal do Windows com C#, VB ou, opcionalmente, C﻿+﻿+.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Nativo | 16.0.28315.86 | Necessária
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 16.0.28315.86 | Necessária
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 16.0.28517.75 | Necessária
Microsoft.Net.Core.Component.SDK.2.1 | Ferramentas de desenvolvimento do .NET Core 2.1 | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Graphics | Editores de imagens e modelos 3D | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnóstico do JavaScript | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Suporte às linguagens JavaScript e TypeScript | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.SQL.CLR | Tipos de dados CLR do SQL Server | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.Component.TypeScript.3.3 | SDK do TypeScript 3.3 | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK.17763 | SDK do Windows 10 (10.0.17763.0) | 16.0.28517.75 | Necessária
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native e .NET Standard | 16.0.28516.191 | Necessária
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Ferramentas da Plataforma Universal do Windows | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Ferramentas da Plataforma Universal do Windows para Xamarin | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 16.0.28621.142 | Necessária
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Opcional
Microsoft.Component.VC.Runtime.OSSupport | Tempo de execução da Plataforma Universal do Windows do C++ para ferramentas de build v142 | 16.0.28625.61 | Opcional
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Graphics.Tools | Depurador de gráficos e criador de perfil de GPU do DirectX | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Suporte da Plataforma Universal do Windows do C++ para ferramentas de build v142 (ARM64) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Atualização dos Pacotes Redistribuíveis do C++ 2019 | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 – ferramentas de build do C++ para VS 2019 ARM (v14.20) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 – ferramentas de build do C++ para VS 2019 ARM64 (v14.20) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 – ferramentas de build do C++ para VS 2017 ARM (v14.16) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 – ferramentas de build do C++ para VS 2017 ARM64 (v14.16) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – ferramentas de build do C++ para VS 2017 x64/x86 (v14.16) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.16299 | SDK do Windows 10 (10.0.16299.0) | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.17134 | SDK do Windows 10 (10.0.17134.0) | 16.0.28517.75 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Conectividade de dispositivos USB | 16.0.28320.51 | Opcional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Principais recursos de área de trabalho do Visual C++ | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Ferramentas da Plataforma Universal do Windows do C++ (v142) | 16.0.28621.142 | Opcional
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Ferramentas da Plataforma Universal do Windows do C++ (v141) | 16.0.28621.142 | Opcional

## <a name="visual-studio-extension-development"></a>Desenvolvimento de extensões do Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrição:** Crie complementos e extensões para o Visual Studio, incluindo novos comandos, analisadores de código e janelas de ferramentas.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.SDK | SDK do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.Component.4.7.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.2 | 16.0.28517.75 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.7.2 | 16.0.28516.191 | Necessária
Microsoft.VisualStudio.Component.NuGet | Gerenciador de pacotes NuGet | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 16.0.28528.71 | Necessária
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.0.28625.61 | Necessária
Microsoft.VisualStudio.Component.VSSDK | SDK do Visual Studio | 16.0.28315.86 | Necessária
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Pré-requisitos para o desenvolvimento de extensões do Visual Studio | 16.0.28621.142 | Necessária
Microsoft.VisualStudio.Component.DiagnosticTools | Ferramentas de criação de perfil do .NET | 16.0.28625.61 | Recomendado
Microsoft.VisualStudio.Component.TextTemplating | Transformação de modelo de texto | 16.0.28625.61 | Recomendado
Component.Dotfuscator | Proteção PreEmptive – Dotfuscator | 16.0.28528.71 | Opcional
Microsoft.Component.CodeAnalysis.SDK | SDK da Plataforma do Compilador .NET | 16.0.28625.61 | Opcional
Microsoft.Component.VC.Runtime.OSSupport | Tempo de execução da Plataforma Universal do Windows do C++ para ferramentas de build v142 | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.AppInsights.Tools | Ferramentas de Análise do Desenvolvedor | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.ClassDesigner | Designer de Classe | 16.0.28528.71 | Opcional
Microsoft.VisualStudio.Component.DslTools | SDK de Modelagem | 16.0.28315.86 | Opcional
Microsoft.VisualStudio.Component.VC.ATL | ATL do C++ para ferramentas de build v142 (x86 e x64) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC do C++ para ferramentas de build v142 (x86 e x64) | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.CoreIde | Funcionalidades principais do C++ | 16.0.28625.61 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 – ferramentas de build do C++ para VS 2019 x64/x86 (v14.20) | 16.0.28625.61 | Opcional

## <a name="unaffiliated-components"></a>Componentes não afiliados

Estes são os componentes que não são incluídos com nenhuma carga de trabalho, mas que podem ser selecionados como um componente individual.

ID do componente | Nome | Versão
--- | --- | ---
Component.GitHub.VisualStudio | Extensão do GitHub para Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Criador de perfil do Xamarin | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.HelpViewer | Visualizador da Ajuda | 16.0.28625.61
Microsoft.NetCore.1x.ComponentGroup.Web | Ferramentas de desenvolvimento do .NET Core 1.0 – 1.1 para Web | 16.0.28621.142
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integração do Azure DevOps ao Office | 16.0.28625.61
Microsoft.VisualStudio.Component.DependencyValidation.Community | Validação de dependência | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git para Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Ferramentas do LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL do C++ para ferramentas de build v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL do C++ para ferramentas de build v142 com Mitigações de Espectro (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL do C++ para ferramentas de build v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL do C++ para ferramentas de build v142 com Mitigações de Espectro (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL do C++ para ferramentas de build v142 com Mitigações de Espectro (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC do C++ para ferramentas de build v142 com Mitigações de Espectro (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC do C++ para ferramentas de build v142 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC do C++ para ferramentas de build v142 com Mitigações de Espectro (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC do C++ para ferramentas de build v142 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | MFC do C++ para ferramentas de build v142 com Mitigações de Espectro (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Redist.MSM | MSMs dos Pacotes Redistribuíveis do C++ 2019 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 – bibliotecas com mitigação de Espectro do C++ para VS 2019 ARM (v14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 – bibliotecas com mitigação de Espectro do C++ para VS 2019 ARM64 (v14.20) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 – bibliotecas com mitigação de Espectro do C++ para VS 2019 x64/x86 (v14.20)  | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 – bibliotecas com mitigação de Espectro do C++ para VS 2017 ARM (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 – bibliotecas com mitigação de Espectro do C++ para VS 2017 ARM64 (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL | ATL do C++ para ferramentas de build v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | ATL do C++ para ferramentas de build v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | ATL do C++ para ferramentas de build v141 com Mitigações de Espectro (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | ATL do C++ para ferramentas de build v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | ATL do C++ para ferramentas de build v141 com Mitigações de Espectro (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | ATL do C++ para ferramentas de build v141 com Mitigações de Espectro (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Suporte do C++/CLI para ferramentas de build v141 | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC | MFC do C++ para ferramentas de build v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | MFC do C++ para ferramentas de build v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | MFC do C++ para ferramentas de build v141 com Mitigações de Espectro (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | MFC do C++ para ferramentas de build v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | MFC do C++ para ferramentas de build v141 com Mitigações de Espectro (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | MFC do C++ para ferramentas de build v141 com Mitigações de Espectro (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 – bibliotecas com mitigação de Espectro do C++ para VS 2017 x64/x86 (v14.16) | 16.0.28625.61
Microsoft.VisualStudio.Component.WinXP | Suporte do Windows XP do C++ para ferramentas do VS 2017 (v141) [Preterido] | 16.0.28625.61
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.0.28621.142
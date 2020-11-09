---
title: Pré-requisitos de implantação do aplicativo | Microsoft Docs
description: Saiba mais sobre os pré-requisitos de implantação para seus aplicativos, incluindo o uso da caixa de diálogo pré-requisitos e dos pacotes de bootstrapper.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c87b0f6ded2960054cb553dbeb85681aa447668b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383242"
---
# <a name="application-deployment-prerequisites"></a>Pré-requisitos de implantação do aplicativo

Para que seu aplicativo seja instalado e executado com êxito, primeiro instale todos os componentes nos quais seu aplicativo depende do computador de destino. Por exemplo, a maioria dos aplicativos criados usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o tem uma dependência na .NET Framework. Nesse caso, a versão correta do Common Language Runtime deve estar presente no computador de destino antes da instalação do aplicativo.

 Você pode selecionar esses pré-requisitos na caixa de **diálogo pré-requisitos** e instalar o .NET Framework e qualquer outro redistribuível como parte de sua instalação. Essa prática é conhecida como *inicialização*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera um programa executável do Windows chamado *Setup.exe* , também conhecido como *bootstrapper*. O bootstrapper é responsável pela instalação desses pré-requisitos antes de executar o aplicativo. Para obter mais informações sobre como selecionar esses pré-requisitos, consulte a [caixa de diálogo pré-requisitos](../ide/reference/prerequisites-dialog-box.md).

 Cada pré-requisito é um pacote de bootstrapper. Um pacote de bootstrapper é um grupo de diretórios e arquivos que contém os arquivos de manifesto que descrevem como os pré-requisitos são instalados. Se os pré-requisitos do aplicativo não estiverem listados na **Caixa de Diálogo de Pré-requisito** , você poderá criar pacotes de bootstrapper personalizados e adicioná-los ao Visual Studio. Em seguida, você pode selecionar os pré-requisitos na **caixa de diálogo Pré-requisitos**. Para obter mais informações, consulte [criar pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md).

 Por padrão, a inicialização está habilitada para implantação do ClickOnce. O bootstrapper gerado para implantação do ClickOnce é assinado. Você pode desabilitar a inicialização de um componente, mas somente se tiver certeza de que a versão correta do componente já está instalada em todos os computadores de destino.

## <a name="bootstrapping-and-clickonce-deployment"></a>Inicialização e implantação do ClickOnce
 Antes de instalar um aplicativo em um computador cliente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o examina o cliente para garantir que ele tenha os requisitos especificados no manifesto do aplicativo. Isso inclui os seguintes requisitos:

- A versão mínima necessária do runtime da linguagem comum, que está especificada como uma dependência do assembly no manifesto do aplicativo.

- A versão mínima necessária do sistema operacional Windows exigida pelo aplicativo, conforme especificado no manifesto do aplicativo usando o elemento `<osVersionInfo>`. (Consulte o [ \<dependency> elemento](../deployment/dependency-element-clickonce-application.md).)

- A versão mínima de todos os assemblies que devem ser pré-instalados no GAC (cache de assembly global), conforme especificado pelas declarações de dependência de assembly no manifesto do assembly.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pode detectar pré-requisitos ausentes e você pode instalar os pré-requisitos usando um bootstrapper. Para obter mais informações, consulte [como: instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Para alterar os valores nos manifestos gerados por ferramentas como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e *MageUI.exe* , você precisa editar o manifesto do aplicativo em um editor de texto e, em seguida, assinar novamente os manifestos de aplicativo e de implantação. Para obter mais informações, consulte [como: assinar novamente manifestos de aplicativo e implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Se você usar o Visual Studio e o ClickOnce para implantar seu aplicativo, os pacotes do bootstrapper selecionados por padrão dependerão da versão do .NET Framework na solução. No entanto, se você alterar a versão do .NET Framework de destino, deverá atualizar as opções na **Caixa de Diálogo Pré-requisitos** manualmente.

|.NET Framework de Destino|Pacotes do Bootstrapper Selecionados|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Com a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, a página *Publish.htm* gerada pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Assistente de publicação aponta para um link que instala apenas o aplicativo ou para um link que instala o aplicativo e os componentes inicializados.

 Se você gerar o bootstrapper usando o assistente de publicação do ClickOnce ou a página de publicação no Visual Studio, a *Setup.exe* será assinada automaticamente. No entanto, se desejar usar o certificado do cliente para assinar o bootstrapper, você poderá assinar o arquivo mais tarde.

## <a name="bootstrapping-and-msbuild"></a>Inicialização e MSBuild
 Se você não usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , mas, em vez disso, compilar seus aplicativos na linha de comando, poderá criar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo de inicialização usando uma tarefa de Microsoft Build Engine (MSBuild). Para obter mais informações, consulte [GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md).

 Como alternativa para a inicialização, você pode pré-implantar componentes usando um sistema de distribuição de software eletrônico, tal como o Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumentos da linha de comando do bootstrapper (Setup.exe)
 O *Setup.exe* gerado pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e as tarefas do MSBuild dão suporte ao seguinte conjunto de argumentos de linha de comando. Todos os outros argumentos são encaminhados para o instalador do aplicativo.

 Se você alterar qualquer opção de bootstrapper, deverá alterar o bootstrapper não assinado e depois assinar o arquivo bootstrapper.

| Argumento de linha de comando | Descrição |
| - | - |
| **-?, -h, -help** | Exibe uma caixa de diálogo de Ajuda. |
| **-url, -componentsurl** | Mostra a URL armazenada e a URL dos componentes para esta configuração. |
| **-URL =**`location` | Define a URL onde *Setup.exe* será procurada pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. |
| **-componentsurl=** `location` | Define a URL onde *Setup.exe* procurará as dependências, como a .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | Quando `true` , o baixa as dependências do local preferido no site do fornecedor. Essa configuração substitui a configuração **-ComponentsUrl** . Quando `false` , o baixa as dependências da URL especificada por **-ComponentsUrl**. |

## <a name="operating-system-support"></a>Suporte do sistema operacional
 Não há suporte para o bootstrapper do Visual Studio no Windows Server 2008 Server Core ou no Windows Server 2008 R2 Server Core, pois eles fornecem um ambiente de servidor de baixa manutenção com funcionalidade limitada. Por exemplo, a opção de instalação Server Core dá suporte apenas ao perfil do .NET Framework Server Core 3,5, que não pode executar os recursos do Visual Studio que dependem do .NET Framework completo.

## <a name="see-also"></a>Confira também
- [Escolher uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
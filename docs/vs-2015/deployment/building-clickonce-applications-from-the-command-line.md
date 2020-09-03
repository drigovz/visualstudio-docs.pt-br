---
title: Criando aplicativos ClickOnce a partir da linha de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2625a8d4caa7dd53e9ce86395a98622f91d686b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155704"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Compilando aplicativos ClickOnce a partir da linha de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , você pode criar projetos a partir da linha de comando, mesmo que eles sejam criados no ambiente de desenvolvimento integrado (IDE). Na verdade, você pode recriar um projeto criado com [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] o em outro computador que tenha apenas o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] instalado. Isso permite que você reproduza uma compilação usando um processo automatizado, por exemplo, em um laboratório de compilação central ou usando técnicas de script avançadas além do escopo da criação do projeto em si.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Usando o MSBuild para reproduzir implantações de aplicativo ClickOnce  
 Quando você invoca o MSBuild/target: publish na linha de comando, ele informa ao sistema MSBuild para compilar o projeto e criar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo na pasta de publicação. Isso é equivalente a selecionar o comando **Publish** no IDE.  
  
 Esse comando executa msbuild.exe, que está no caminho no ambiente de prompt de comando do Visual Studio.  
  
 Um "destino" é um indicador do MSBuild sobre como processar o comando. Os principais destinos são o destino "Build" e o destino "Publish". O destino da compilação é o equivalente a selecionar o comando de compilação (ou pressionar F5) no IDE. Se você quiser apenas compilar seu projeto, poderá conseguir isso digitando `msbuild` . Esse comando funciona porque o destino da compilação é o destino padrão para todos os projetos gerados pelo [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Isso significa que você não precisa especificar explicitamente o destino da compilação. Portanto, digitar `msbuild` é a mesma operação que digitar `msbuild /target:build` .  
  
 O `/target:publish` comando informa ao MSBuild para invocar o destino de publicação. O destino de publicação depende do destino da compilação. Isso significa que a operação de publicação é um superconjunto da operação de compilação. Por exemplo, se você fez uma alteração em um dos arquivos de origem Visual Basic ou C#, o assembly correspondente seria automaticamente recriado pela operação de publicação.  
  
 Para obter informações sobre como gerar uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação completa usando a ferramenta de linha de comando Mage.exe para criar seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto, consulte [passo a passos: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Criando e compilando um aplicativo ClickOnce básico usando o MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Para criar e publicar um projeto ClickOnce  
  
1. Clique em **novo projeto** no menu **arquivo** . A caixa de diálogo **Novo Projeto** aparecerá.  
  
2. Selecione **aplicativo do Windows** e nomeie-o `CmdLineDemo` .  
  
3. No menu **Compilar** , clique no comando **publicar** .  
  
    Essa etapa garante que o projeto esteja configurado corretamente para produzir uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação de aplicativo.  
  
    O Assistente de Publicação será exibido.  
  
4. No assistente de publicação, clique em **concluir**.  
  
    O Visual Studio gera e exibe a página da Web padrão, chamada Publish.htm.  
  
5. Salve seu projeto e anote o local da pasta em que ele está armazenado.  
  
   As etapas acima criam um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projeto que foi publicado pela primeira vez. Agora você pode reproduzir a compilação fora do IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Para reproduzir a compilação a partir da linha de comando  
  
1. Saia do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
2. No menu **Iniciar** do Windows, clique em **todos os programas**, **Microsoft Visual Studio**, em seguida, **Ferramentas do Visual Studio**, em seguida, prompt de **comando do Visual Studio**. Isso deve abrir um prompt de comando na pasta raiz do usuário atual.  
  
3. No **prompt de comando do Visual Studio**, altere o diretório atual para o local do projeto que você acabou de criar acima. Por exemplo, digite `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4. Para remover os arquivos existentes produzidos em "para criar e publicar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] projeto", digite `rmdir /s publish` .  
  
    Essa etapa é opcional, mas garante que os novos arquivos foram todos produzidos pela compilação de linha de comando.  
  
5. Digite `msbuild /target:publish`.  
  
   As etapas acima produzirão uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação completa do aplicativo em uma subpasta do projeto chamada **Publish**. CmdLineDemo. Application é o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto de implantação. A pasta CmdLineDemo_1.0.0.0 contém os arquivos CmdLineDemo.exe e CmdLineDemo.exe. manifest, o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto do aplicativo. Setup.exe é o bootstrapper, que, por padrão, é configurado para instalar o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . A pasta DotNetFX contém os pacotes redistribuíveis para o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Esse é o conjunto inteiro de arquivos de que você precisa para implantar seu aplicativo na Web ou via UNC ou CD/DVD.  
  
## <a name="publishing-properties"></a>Propriedades de publicação  
 Quando você publica o aplicativo nos procedimentos acima, as propriedades a seguir são inseridas em seu arquivo de projeto pelo assistente de publicação. Essas propriedades influenciam diretamente como o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo é produzido.  
  
 Em CmdLineDemo. vbproj/CmdLineDemo. csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Você pode substituir qualquer uma dessas propriedades na linha de comando sem alterar o próprio arquivo do projeto. Por exemplo, o seguinte compilará a [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação do aplicativo sem o bootstrapper:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 As propriedades de publicação são controladas nas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] páginas de propriedades de **publicação**, **segurança**e **assinatura** do **Designer de projeto**. Abaixo está uma descrição das propriedades de publicação, juntamente com uma indicação de como cada uma é definida nas várias páginas de propriedades do designer de aplicativo:  
  
- `AssemblyOriginatorKeyFile` determina o arquivo de chave usado para assinar os [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestos do aplicativo. Essa mesma chave também pode ser usada para atribuir um nome forte aos seus assemblies. Essa propriedade é definida na página de **assinatura** do **Designer de projeto**.  
  
  As propriedades a seguir são definidas na página **segurança** :  
  
- **Habilitar configurações de segurança do ClickOnce** determina se os [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestos são gerados. Quando um projeto é inicialmente criado, a [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] geração de manifesto é desativada por padrão. O assistente ativará esse sinalizador automaticamente quando você publicar pela primeira vez.  
  
- **TargetZone** determina o nível de confiança a ser emitido no manifesto do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo. Os valores possíveis são "Internet", "LocalIntranet" e "Custom". Internet e LocalIntranet farão com que um conjunto de permissões padrão seja emitido no [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto do aplicativo. LocalIntranet é o padrão e basicamente significa confiança total. Personalizado especifica que apenas as permissões especificadas explicitamente no arquivo. manifest do aplicativo base devem ser emitidas no manifesto do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo. O arquivo app. manifest é um arquivo de manifesto parcial que contém apenas as definições de informações de confiança. É um arquivo oculto, adicionado automaticamente ao seu projeto quando você configura permissões na página **segurança** .  
  
  As propriedades a seguir são definidas na página **publicar** :  
  
- `PublishUrl` é o local onde o aplicativo será publicado no IDE. Ele será inserido no [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto do aplicativo se nem a `InstallUrl` `UpdateUrl` propriedade ou for especificada.  
  
- `ApplicationVersion` Especifica a versão do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo. Este é um número de versão de quatro dígitos. Se o último dígito for um "*", o `ApplicationRevision` será substituído pelo valor inserido no manifesto no momento da compilação.  
  
- `ApplicationRevision` Especifica a revisão. Esse é um inteiro que é incrementado cada vez que você publica no IDE. Observe que ele não é incrementado automaticamente para compilações executadas na linha de comando.  
  
- `Install` Determina se o aplicativo é um aplicativo instalado ou um aplicativo de execução da Web.  
  
- `InstallUrl` (não mostrado) é o local do qual os usuários instalarão o aplicativo. Se especificado, esse valor será gravado no bootstrapper de setup.exe se a `IsWebBootstrapper` propriedade estiver habilitada. Ele também será inserido no manifesto do aplicativo se o `UpdateUrl` não for especificado.  
  
- `SupportUrl` (não mostrado) é o local vinculado na caixa de diálogo **Adicionar/remover programas** para um aplicativo instalado.  
  
  As propriedades a seguir são definidas na caixa de diálogo **atualizações do aplicativo** , acessadas na página **publicar** .  
  
- `UpdateEnabled` indica se o aplicativo deve verificar se há atualizações.  
  
- `UpdateMode` Especifica atualizações em primeiro plano ou atualizações em segundo plano.  
  
- `UpdateInterval` Especifica com que frequência o aplicativo deve verificar se há atualizações.  
  
- `UpdateIntervalUnits` Especifica se o `UpdateInterval` valor está em unidades de horas, dias ou semanas.  
  
- `UpdateUrl` (não mostrado) é o local do qual o aplicativo receberá atualizações. Se especificado, esse valor será inserido no manifesto do aplicativo.  
  
- As propriedades a seguir são definidas na caixa de diálogo **Opções de publicação** , acessadas na página **publicar** .  
  
- `PublisherName` Especifica o nome do publicador exibido no prompt mostrado ao instalar ou executar o aplicativo. No caso de um aplicativo instalado, ele também é usado para especificar o nome da pasta no menu **Iniciar** .  
  
- `ProductName` Especifica o nome do produto exibido no prompt mostrado ao instalar ou executar o aplicativo. No caso de um aplicativo instalado, ele também é usado para especificar o nome do atalho no menu **Iniciar** .  
  
- As propriedades a seguir são definidas na caixa de diálogo **pré-requisitos** , acessada na página **publicar** .  
  
- `BootstrapperEnabled` Determina se o bootstrapper de setup.exe deve ser gerado.  
  
- `IsWebBootstrapper` Determina se o bootstrapper setup.exe funciona na Web ou em modo baseado em disco.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL e UpdateURL  
 A tabela a seguir mostra as quatro opções de URL para implantação do ClickOnce.  
  
|Opção de URL|Descrição|  
|----------------|-----------------|  
|`PublishURL`|Necessário se você estiver publicando seu aplicativo ClickOnce em um site da Web.|  
|`InstallURL`|Opcional. Defina essa opção de URL se o site de instalação for diferente do `PublishURL` . Por exemplo, você pode definir o `PublishURL` para um caminho de FTP e definir o `InstallURL` como uma URL da Web.|  
|`SupportURL`|Opcional. Defina essa opção de URL se o site de suporte for diferente do `PublishURL` . Por exemplo, você pode definir o `SupportURL` para o site de suporte ao cliente da sua empresa.|  
|`UpdateURL`|Opcional. Defina essa opção de URL se o local de atualização for diferente do `InstallURL` . Por exemplo, você pode definir o `PublishURL` para um caminho de FTP e definir o `UpdateURL` como uma URL da Web.|  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

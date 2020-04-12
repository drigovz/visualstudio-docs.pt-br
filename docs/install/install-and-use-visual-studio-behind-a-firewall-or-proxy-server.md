---
title: Instalar e usar por trás de um firewall ou servidor proxy
description: Examine as URLs de domínio, as portas e os protocolos que você pode querer adicionar a uma lista de permissões ou abrir se sua organização usar um firewall ou um servidor proxy
ms.date: 02/01/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 025cf432912d38976507c93545e7c38b44d86fd8
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223652"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Instalar e usar o Visual Studio e os Serviços do Azure atrás de um firewall ou servidor proxy

Se você ou sua organização usa medidas de segurança como um firewall ou um servidor proxy, há URLs de domínio que você talvez queira adicionar a uma "lista de permissões" e portas e protocolos que talvez você queira abrir para que tenha a melhor experiência ao instalar e usar o Visual Studio e os Serviços do Azure.

* **[Instale o Visual Studio](#install-visual-studio)**: Essas tabelas incluem os URLs de domínio para adicionar a uma lista de desemite para que você tenha acesso a todos os componentes e cargas de trabalho desejadas.

* **[Use o Visual Studio e o Azure Services](#use-visual-studio-and-azure-services)**: Esta tabela inclui os URLs de domínio para adicionar a uma lista de permitir e as portas e protocolos a serem abertos para que você tenha acesso a todos os recursos e serviços que deseja.

> [!NOTE]
> Este artigo foi escrito para o Visual Studio no Windows, mas determinadas informações também são aplicáveis à [instalação do Visual Studio para Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) por trás de um firewall ou de um servidor proxy.

## <a name="install-visual-studio"></a>Instalar o Visual Studio

### <a name="urls-to-add-to-an-allow-list"></a>URLs para adicionar a uma lista de permissões

Como o Instalador do Visual Studio baixa arquivos de vários domínios e seus servidores de download, aqui estão as URLs que talvez você deseje adicionar a uma lista de permissões como confiáveis na interface do usuário ou em seus scripts de implantação.

#### <a name="microsoft-domains"></a>Domínios da Microsoft

| Domínio | Finalidade |
| - | - |
| go.microsoft.com | Resolução da URL de instalação |
| aka.ms | Resolução da URL de instalação |
| download.visualstudio.microsoft.com | Local de download de pacotes de instalação |
| download.microsoft.com | Local de download de pacotes de instalação |
| download.visualstudio.com | Local de download de pacotes de instalação |
| dl.xamarin.com | Local de download de pacotes de instalação |
| xamarin-downloads.azureedge.net | Android SDK pacotes localização lista de download |
| marketplace.visualstudio.com | Local de download de extensões do Visual Studio |
| \*Gallerycdn.vsassets.io  | Local de download de extensões do Visual Studio |
| visualstudio.microsoft.com | Local da documentação |
| docs.microsoft.com | Local da documentação |
| msdn.microsoft.com | Local da documentação |
| www\.microsoft.com | Local da documentação |
| \*.windows.net | Local de conexão |
| \*.microsoftonline.com | Local de conexão |
| \*.live.com | Local de conexão |
| | |

#### <a name="non-microsoft-domains"></a>Domínios que não são da Microsoft

| Domínio | Instala essas cargas de trabalho |
| - | - |
| archive.apache.org | Desenvolvimento móvel com JavaScript (Cordova) |
| cocos2d-x.org | Desenvolvimento de jogos com C++ (Cocos) |
| download.epicgames.com | Desenvolvimento de jogos com C++ (Unreal Engine) |
| download.oracle.com | Desenvolvimento móvel com JavaScript (SDK do Java) <br /><br />Desenvolvimento móvel com .NET (SDK do Java) |
| download.unity3d.com | Desenvolvimento de jogos com Unity (Unity) |
| netstorage.unity3d.com | Desenvolvimento de jogos com Unity (Unity) |
| dl.google.com | Desenvolvimento móvel com JavaScript (NDK e SDK do Android, Emulador) <br /><br />Desenvolvimento móvel com .NET (NDK e SDK do Android, Emulador) |
| www\.incredibuild.com | Desenvolvimento de jogos com C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Desenvolvimento de jogos com C++ (IncrediBuild) |
| www\.python.org | Desenvolvimento do Python (Python) <br /><br />Ciência de dados e aplicativos analíticos (Python) |
| developerservices2.apple.com | Provisionamento Xamarin.iOS |
| developer.apple.com | Provisionamento Xamarin.iOS |
| appstoreconnect.apple.com | Provisionamento Xamarin.iOS |
| idmsa.apple.com | Provisionamento Xamarin.iOS |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Usar o Visual Studio e Serviços do Azure

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>URLs a serem adicionadas a uma lista de permissões e portas e protocolos a serem abertos

Para garantir que você tenha acesso a tudo o que deseja quando usar o Visual Studio ou os Serviços Azure atrás de um firewall ou servidor proxy, aqui estão as URLs que você deve adicionar a uma lista de permitir e as portas e protocolos que você pode querer abrir.

| Cenário ou serviço | Ponto de extremidade DNS | Protocolo<br/>/Port | Descrição |
| - | - | -: | - | - |
| URL<br>resolução | go.microsoft.com<br><br>aka.ms | | Usada para reduzir as URLs, que, em seguida, resolvem em URLs mais longas |
| Start Page | vsstartpage.blob.core.windows.net | 443 | Usada para exibir as Novidades do Desenvolvedor mostradas na página inicial (somente Visual Studio 2017) |
| Destino<br> Notification <br>Serviço | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Usada para filtrar uma lista global de notificações para uma lista aplicável somente a tipos específicos de cenários de uso/computadores |
| Extensão <br>verificação de atualização | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Usada para fornecer notificações quando uma extensão instalada tem uma atualização disponível <br><br> Usada como um local de conexão |
| Projeto do AI <br>Integração | az861674.vo.msecnd.net | 443<br> | Usada para configurar novos projetos para enviar dados de uso para sua conta do Application Insights registrada |
| CodeLens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Usada para fornecer informações no editor sobre quando um arquivo foi atualizado pela última, a linha do tempo de alterações, os itens de trabalho aos quais as alterações estão associadas, os autores e muito mais |
| Habilitação <br>de recurso experimental | visualstudio-devdiv-c2s.msedge.net | 80 | Usada para ativar novos recursos experimentais ou alterações de recurso |
| "Crachá" de identidade <br>(nome de usuário e avatar)<br>e <br>Configurações de roaming | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | Usada para exibir o nome do usuário e o avatar no IDE <br><br> Usada para garantir que as alterações de configuração atravessem de um computador para outro |
| Configurações Remotas | az700632.vo.msecnd.net | 443 | Usada para desativar extensões que são conhecidas por causar problemas no Visual Studio |
| Ferramentas do Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Usada para cenários de armazenamento de aplicativos do Windows |
| Esquema JSON <br>Descoberta <br><br>Esquema JSON <br>Definição<br><br>Esquema JSON <br>O suporte para <br>Recursos do Azure | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Usada para descobrir e baixar os esquemas JSON que o usuário pode usar durante a edição de documentos JSON <br><br>Usada para obter o esquema de metavalidação para JSON<br><br>Usada para obter o esquema atual para modelos de implantação do Azure Resource Manager |
| Pacote NPM <br>descoberta | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | Necessária para pesquisar pacotes NPM e usada para a instalação do pacote de script do lado do cliente em projetos da Web |
| Pacote de Bower<br> ícones<br><br>Pacote de Bower <br>pequisa | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Fornece o ícone padrão do pacote de Bower  <br><br>Fornece a capacidade de pesquisar pacotes de Bower |
| NuGet<br><br>Pacote NuGet<br> descoberta | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | Usada para verificar pacotes NuGet assinados.<br><br>Necessária para pesquisar versões e pacotes NuGet |
| Informações do repositório GitHub | api.github.com | https/443 | Necessária para obter informações adicionais sobre pacotes de Bower |
| Linters da Web | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Criação do projeto do<br>Explorador do Cookiecutter<br>descoberta <br><br>Criação do projeto do <br>Explorador do Cookiecutter<br> criação  | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Usada para descobrir modelos online de nosso feed recomendado e de repositórios GitHub <br><br>Usada para criar um projeto de um modelo de cookiecutter que requer uma instalação sob demanda única de um pacote do Python de cookiecutter do PyPI (índice de pacote do Python) |
| Pacote do Python <br>descoberta<br><br>Pacote do Python <br>gerenciamento<br><br>Novo <br>Python <br> project <br>modelos | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | Fornece a capacidade de pesquisar pacotes de pip<br><br>Usada para instalar o pip automaticamente se ele estiver ausente <br><br>Usada para resolver os seguintes novos modelos de projeto do Python para URLs de modelo do cookiecutter:<br> – Projeto de classificador<br>– Projeto de clustering <br> – Projeto de regressão <br> – PyGame usando PyKinect <br> – Projeto Pyvot |
| Web do Office <br>add-in <br> Manifest <br>Verificação <br>Serviço | verificationservice.osi.office.net | https/443 | Usada para validar os manifestos de suplementos de Web do Office |
| Suplementos do SharePoint <br>e do Office | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 | Usado para publicar e testar Add-ins do SharePoint e do Office no SharePoint Online e no Office 365 |
| Serviço de teste do <br>Gerenciador de Fluxo de Trabalho<br> Host | | http/12292 | Uma regra de firewall que é criada automaticamente para testar suplementos do SharePoint com fluxos de trabalho |
| Estatísticas de confiabilidade <br>coletadas automaticamente <br>e outros <br>CEIP (Programas de Aperfeiçoamento da <br>Experiência do Usuário)<br> para o SDK do Azure <br>para Ferramentas do SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Usada para enviar as estatísticas de confiabilidade (dados de travamento ou falha) do usuário à Microsoft. Os despejos de travamento/falha reais ainda serão carregados se o Relatório de Erros do Windows estiver habilitado, apenas informações estatísticas serão suprimidas; <br>Usada para revelar padrões de uso anônimos para a extensão do SDK de Ferramentas do Azure para o Visual Studio e para padrões de uso para ferramentas do SQL para Visual Studio |
| Visual Studio <br> CEIP (Programas de Aperfeiçoamento da <br>Experiência do Usuário) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Usada para coletar logs de erro e padrões de uso anônimos <br><br>Usada para rastrear problemas de congelamento da interface do usuário |
| Criação e<br>Gerenciamento de <br>Recursos do Azure | management.azure.com <br>management.core.windows.net | https/443 | Usada para criar sites do Azure ou outros recursos para dar suporte à publicação de aplicativos Web, Azure Functions ou WebJobs |
| Recomendações de <br>extensão e verificações de <br>filmes | marketplace.visualstudio.com | https/443 | Usada para verificar a disponibilidade de ferramentas de publicação atualizadas. Se desabilitada, uma potencial extensão recomendada para publicação Web poderá não ser mostrada |
| Informações de ponto de extremidade de criação <br>de Recurso do Azure atualizadas | \*.blob.core.windows.net | https/443 | Usada para atualizar os pontos de extremidade usados para a criação de Recursos do Azure para determinados Serviços do Azure. Se desabilitada, as últimas localizações de ponto de extremidade baixadas ou inseridas são usadas |
| Depuração remota e <br>Criação de perfil remota de <br>Websites do Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Usada para anexar o depurador remoto a sites do Azure. Se desabilitada, a anexação do depurador remoto a sites do Azure não funcionará |
| Active Directory <br>Grafo | graph.windows.net | https/443 | Usada para provisionar novos aplicativos do Azure Active Directory. Também usado pelo provedor de serviço conectado MSGraph do Office 365 |
| Funções do Azure <br>Atualização de CLI do <br>Verificação | functionscdn.azureedge.net | https/443 | Usada para verificar as versões atualizadas da CLI do Azure Functions. Se desabilitada, uma cópia armazenada em cache (ou a cópia carregada pelo componente do Azure Functions) da CLI será usada |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | O HTTP é usado para downloads de Gradle durante o build. O HTTPS é usado para incluir plug-ins do Cordova nos projetos |
| Gerenciador de Nuvem | 1. &#60;ponto de extremidade do cluster&#62; <br>Service Fabric <br>2. &#60;ponto de extremidade de gerenciamento&#62;<br>General Cloud Exp <br>3. &#60;ponto de extremidade do grafo&#62;<br>General Cloud Exp<br>4. &#60;ponto de extremidade da conta de armazenamento&#62;<br>Nós de Armazenamento <br>5. &#60;Azure portal URLs&#62;<br>General Cloud Exp <br>6. &#60;pontos de extremidade do key vault&#62; <br>Nós de VM do Azure Resource Manager<br>7. &#60;Endereço de IP pública do cluster&#62;<br>Depuração remota do Service Fabric e Rastreamentos de ETW | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7.tcp/dinâmico | 1. Exemplo: test12.eastus.cloudapp.com<br>2. Recupera assinaturas e recupera/gerencia recursos do Azure<br>3. Recupera assinaturas do Azure Stack<br>4. Gerencia recursos de armazenamento (exemplo: mystorageaccount.blob.core.windows.net)<br>5. Opção de menu de contexto "Abrir no Portal" (abre um recurso no portal Azure)<br>6. Cria e usa cofres-chave para depuração de VM (Exemplo: myvault.vault.azure.net) <br><br>7. Aloca dinamicamente o bloco de portas com base no número de nós no cluster e nas portas disponíveis. <br><br>Um bloco de portas tentará obter três vezes o número dos nós com um mínimo de 10 portas.<br><br>Para rastreamentos de Streaming, é feita uma tentativa para obter o bloco de portas de 810. Se qualquer um dos blocos de portas já estiver em uso, será feita uma tentativa de obter o próximo bloco e assim por diante. (O balanceador de carga está vazio, então as portas de 810 provavelmente serão usadas) <br><br>Da mesma forma para depuração, quatro conjuntos de blocos de portas são reservados: <br>- connectorPort: 30398, <br>- forwarderPort: 31398, <br>- forwarderPortx86: 31399,<br>- fileUploadPort: 32398<br> |
| Serviços de Nuvem | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;serviço de nuvem do usuário&#62;.cloudapp.net <br> &#60;VM do usuário&#62;.&#60;região&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Área de trabalho remota para VM serviços de nuvem <br><br> 2. Componente da conta de armazenamento da configuração de diagnóstico privado <br><br> 3. Portal Azure <br><br> 4. Server Explorer - Azure Storage &#42; é uma conta de armazenamento nomeada pelo cliente  <br><br> 5. Links para abrir o portal &#47; Baixe o certificado de assinatura &#47; publicar o arquivo de configurações <br><br>6. a) Porta local do conector para depuração remota para serviço de nuvem e VM<br> 6. b) Porta pública do conector para depuração remota para serviço de nuvem e VM <br> 6. c) Porta local do encaminhador para depuração remota para serviço de nuvem e VM <br> 6. d) Porta pública do encaminhador para depuração remota para serviço de nuvem e VM  <br> 6. e) Porta local do carregador de arquivos para depuração remota para serviço de nuvem e VM <br> 6. f) Porta pública do carregador de arquivos para depuração remota para serviço de nuvem e VM |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 | 1. Documentação <br><br> 2. Criar recurso de cluster <br><br>3. O &#42; é o nome do cofre da chave Azure (Exemplo:- test11220180112110108.vault.azure.net  <br><br>  4. O &#42; é dinâmico (Exemplo: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Instantâneo <br>Depurador | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. Endereço IP de serviços/servidores remotos/FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. Concord/<br> 4022 (versão visual studio dependente) | 1. Arquivo .json de consulta para o tamanho do SKU do serviço de aplicativo <br>2. Várias chamadas azure RM <br>3. Chamada de aquecimento do site via  <br>4. O ponto final do Serviço de Aplicativo Kudu direcionado pelo cliente <br>5. Versão de extensão do site de consulta publicada em nuget.org <br>6. [Depuração remota](../debugger/remote-debugging.md) |
| Stream Analytics do Azure <br><br>HDInsight | Management.azure.com | https/443 | Usada para exibir, enviar, executar e gerenciar trabalhos ASA <br><br> Usada para navegar em clusters HDI e enviar, diagnosticar e depurar trabalhos HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 | Usada para compilar, enviar, exibir, diagnosticar e depurar os trabalhos, usada para navegar em arquivos ADLS, usada para carregar e baixar arquivos |
| Empacotar serviço | [conta].visualstudio.com <br/> [conta].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | Os \*.npmjs.org, \*.nuget.org \*e .nodejs.org são necessários apenas para determinados cenários de tarefa de construção (por exemplo: NuGet Tool Installer, Node Tool Installer) ou se você pretende usar o público upstream com seus Feeds. Os outros três domínios são necessários para a funcionalidade principal do serviço de empacotamento. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Usado para conectar-se ao Azure DevOps Services |
| Comunidade de Desenvolvedores | sendvsfeedback2.azurewebsites.net/api | https/443 | Usado para chamar APIs de ferramenta de feedback da comunidade do desenvolvedor (meus problemas, pesquisa, voto, comentário, envio, upload, currículo) |
| Intellicode | \*Intellicode.vsengsaas.visualstudio.com | https/443 | Usado para chamar APIs intellicode |
| Live Share | \*liveshare.vsengsaas.visualstudio.com.| https/443 | Usado para chamar APIs de compartilhamento ao vivo |
| Visual Studio Online | \*Online.visualstudio.com | https/443 | Usado para chamar APIs online do Visual Studio |
| Aquisição automática de tipo JavaScript | registry.npmjs.org | https/443 | Usado para instalar definições de tipo TypeScript para fornecer Intellisense para bibliotecas JavaScript populares |
| Serviço de licenciamento de assinaturas do Visual Studio | app.vssps.visualstudio.com/apis/<br/>Licenciamento/Direitos do Cliente | https/443 | Licenciamento para ativação on-line |
| Depurador | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon. \*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>Usado para baixar bits de depurador para depuração .NET Core no Unix / macOS sobre SSH <br><br>2. <br>Usado para baixar bits de depurador para depuração remota de contêineres do Windows Docker<br><br> 3. Usado para a revisão da fonte da estrutura .NET <br><br> 4. <br>(Se o usuário optar por entrar) Usado para baixar símbolos publicados para nuget.org servidor símbolo.<br><br> 5. (Se o usuário optar por entrar) Usado para baixar símbolos e binários de MS, também pode ser necessário para depurar código gerenciado em lixões |
| Visual Studio Online| \*Online.visualstudio.com | https/443 | Usado para chamar APIs online do Visual Studio |
| Xamarin Android App Publishing | \*Googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Usado para interagir com o serviço Google Play Store para publicar/carregar aplicativos Xamarin Android diretamente do Visual Studio. |
| Registro de Contêiner do Azure | *.azurecr.io | https/443 | Registros de contêineres de acesso hospedados no Azure, para configuração de gasodutos CICD |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Solucionar problemas de erros relacionados à rede

Às vezes, você pode encontrar erros relacionados à rede ou ao proxy ao instalar ou usar o Visual Studio atrás de um firewall ou servidor proxy. Para obter mais informações sobre as soluções para essas mensagens de erro, consulte a página [Solução de erros relacionados à rede ao instalar ou usar o Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Obtenha suporte

Oferecemos uma opção [**de suporte de chat de instalação**](https://visualstudio.microsoft.com/vs/support/#talktous) (somente em inglês) para problemas relacionados à instalação.

Aqui estão algumas outras opções de suporte:

* Relate problemas do produto para nós por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Sugira um recurso, acompanhe os problemas do produto e encontre respostas na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/).
* Use sua conta do [GitHub](https://github.com/) para falar conosco e com outros desenvolvedores do Visual Studio nas [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Confira também

* [Requisitos de conectividade do Live Share](/visualstudio/liveshare/reference/connectivity/)
* [Criar uma instalação de rede do Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Solução de erros relacionados à rede no Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Instalar por trás de um firewall ou de um servidor proxy (Visual Studio para Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

---
title: Referência do Esquema de Extensão VSIX 2.0 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697922"
---
# <a name="vsix-extension-schema-20-reference"></a>Referência do esquema de extensão VSIX 2.0
Um arquivo manifesto de implantação VSIX descreve o conteúdo de um pacote VSIX. O formato do arquivo é regido por um esquema. A versão 2.0 deste esquema suporta a adição de tipos e atributos personalizados.  O esquema do manifesto é extensível. O carregador manifesto ignora elementos XML e atributos que ele não entende.

> [!IMPORTANT]
> Visual Studio 2015 pode carregar arquivos VSIX nos formatos Visual Studio 2010, Visual Studio 2012 ou Visual Studio 2013.

## <a name="package-manifest-schema"></a>Esquema de manifesto de pacote
 O elemento raiz do arquivo `<PackageManifest>`Manifest XML é . Ele tem um `Version`único atributo, que é a versão do formato manifesto. Se forem feitas grandes alterações no formato, o formato da versão será alterado. Este artigo descreve o formato manifesto versão 2.0, que `Version` é especificado no manifesto definindo o atributo para o valor de Version="2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 Dentro `<PackageManifest>` do elemento raiz, você pode usar os seguintes elementos:

- `<Metadata>`- Metadados e informações publicitárias sobre o pacote em si. Apenas `Metadata` um elemento é permitido no manifesto.

- `<Installation>`- Esta seção define a forma como este pacote de extensão pode ser instalado, incluindo o aplicativo SKUs em que ele pode instalar. Apenas um `Installation` único elemento é permitido no manifesto. Um manifesto deve `Installation` ter um elemento, ou este pacote não será instalado em nenhum SKU.

- `<Dependencies>`- Uma lista opcional de dependências para este pacote é definida aqui.

- `<Assets>`- Esta seção contém todos os ativos contidos neste pacote. Sem esta seção, este pacote não surgirá nenhum conteúdo.

- `<AnyElement>*`- O esquema manifesto é flexível o suficiente para permitir quaisquer outros elementos. Quaisquer elementos infantis não reconhecidos pelo carregador manifesto são expostos na API do Gerenciador de extensão como objetos XmlElement extras. Usando esses elementos crianças, as extensões VSIX podem definir dados adicionais no arquivo manifesto que o código em execução no Visual Studio pode acessar em tempo de execução. Consulte [microsoft.visualstudio.extensionmanager.iExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Elemento de metadados
 Esta seção são os metadados sobre o pacote, sua identidade e informações publicitárias. `<Metadata>`contém os seguintes elementos:

- `<Identity>`- Define as informações de identificação deste pacote e inclui os seguintes atributos:

  - `Id`- Este atributo deve ser um ID único para o pacote escolhido pelo seu autor. O nome deve ser qualificado da mesma forma que os tipos CLR são espaçados: Company.Product.Feature.Name. O `Id` atributo é limitado a 100 caracteres.

  - `Version`- Define a versão deste pacote e seu conteúdo. Este atributo segue o formato de versão de montagem CLR: Major.Minor.Build.Revision (1.2.40308.00). Um pacote com um número de versão mais alto é considerado atualizações para o pacote, e pode ser instalado sobre a versão instalada existente.

  - `Language`- Este atributo é a linguagem padrão do pacote e corresponde aos dados texulos neste manifesto. Este atributo segue a convenção de código local da CLR para assembléias de recursos, por exemplo: en-us, en, fr-fr. Você pode `neutral` especificar para declarar uma extensão neutra em idioma que será executada em qualquer versão do Visual Studio. O valor padrão é `neutral`.

  - `Publisher`- Este atributo identifica o editor deste pacote, seja uma empresa ou nome individual. O `Publisher` atributo é limitado a 100 caracteres.

- `<DisplayName>`- Este elemento especifica o nome do pacote fácil de usar que é exibido na ui do Gerenciador de extensão. O `DisplayName` conteúdo é limitado a 50 caracteres.

- `<Description>`- Este elemento opcional é uma breve descrição do pacote e seu conteúdo que é exibido na ID do Gerenciador de Extensão. O `Description` conteúdo pode conter qualquer texto que você quiser, mas é limitado a 1000 caracteres.

- `<MoreInfo>`- Este elemento opcional é uma URL para uma página on-line que contém uma descrição completa deste pacote. O protocolo deve ser especificado como http.

- `<License>`- Este elemento opcional é um caminho relativo para um arquivo de licença (.txt, .rtf) contido no pacote.

- `<ReleaseNotes>`- Este elemento opcional é um caminho relativo para um arquivo de notas de versão contido no pacote (.txt, .rtf) ou então uma URL para um site que exibe as notas de versão.

- `<Icon>`- Este elemento opcional é um caminho relativo para um arquivo de imagem (png, bmp, jpeg, ico) contido no pacote. A imagem do ícone deve ser de 32x32 pixels (ou será reduzida a esse tamanho) e aparece na lista de ida e outra. Se `Icon` nenhum elemento for especificado, a ui usará um padrão.

- `<PreviewImage>`- Este elemento opcional é um caminho relativo para um arquivo de imagem (png, bmp, jpeg) contido no pacote. A imagem de visualização deve ser de 200x200 pixels, e exibida nos detalhes UI. Se `PreviewImage` nenhum elemento for especificado, a ui usará um padrão.

- `<Tags>`- Este elemento opcional lista marcas de texto delimitadas em ponto e vírgula adicionais que são usadas para dicas de pesquisa. O `Tags` elemento é limitado a 100 caracteres.

- `<GettingStartedGuide>`- Este elemento opcional é um caminho relativo para um arquivo HTML ou uma URL para um site que contém informações sobre como usar a extensão ou conteúdo dentro deste pacote. Este guia é lançado como parte de uma instalação.

- `<AnyElement>*`- O esquema manifesto é flexível o suficiente para permitir quaisquer outros elementos. Quaisquer elementos infantis que não são reconhecidos pelo carregador manifesto são expostos como uma lista de objetos XmlElement. Usando esses elementos crianças, as extensões VSIX podem definir dados adicionais no arquivo manifesto e enumerar-os em tempo de execução.

### <a name="installation-element"></a>Elemento de instalação
 Esta seção define a forma como este pacote pode ser instalado e o aplicativo SKUs em que ele pode instalar. Esta seção contém os seguintes atributos:

- `Experimental`- Defina este atributo como verdadeiro se você tiver uma extensão que está atualmente instalada para todos os usuários, mas você está desenvolvendo uma versão atualizada no mesmo computador. Por exemplo, se você instalou o MyExtension 1.0 para todos os usuários, mas deseja depurar o MyExtension 2.0 no mesmo computador, defina Experimental="true". Este atributo está disponível no Visual Studio 2015 Update 1 e posterior.

- `Scope`- Este atributo pode levar o valor "Global" ou "ProductExtension":

  - "Global" especifica que a instalação não está escopo para um SKU específico. Por exemplo, esse valor é usado quando um SDK de extensão é instalado.

  - "ProductExtension" especifica que uma extensão VSIX tradicional (versão 1.0) escopo para SKUs visual individual está instalada. Esse é o valor padrão.

- `AllUsers`- Este atributo opcional especifica se este pacote será instalado para todos os usuários. Por padrão, este atributo é falso, o que especifica que o pacote é por usuário. (Quando você define esse valor como verdadeiro, o usuário instalado deve elevar-se ao nível de privilégio administrativo para instalar o VSIX resultante.

- `InstalledByMsi`- Este atributo opcional especifica se este pacote está instalado por um MSI. Os pacotes instalados por um MSI são instalados e gerenciados pelo MSI (Programas e Recursos) e não pelo Visual Studio Extension Manager.  Por padrão, este atributo é falso, o que especifica que o pacote não está instalado por um MSI.

- `SystemComponent`- Este atributo opcional especifica se este pacote deve ser considerado um componente do sistema. Os componentes do sistema não aparecem na ui do Gerenciador de extensão e não podem ser atualizados. Por padrão, este atributo é falso, o que especifica que o pacote não é um componente do sistema.

- `AnyAttribute*`- `Installation` O elemento aceita um conjunto aberto de atributos que serão expostos em tempo de execução como um dicionário de par de valor de nome.

- `<InstallationTarget>`-Este elemento controla o local onde o instalador VSIX instala o pacote. Se o valor `Scope` do atributo for "ProductExtension" o pacote deve ter como alvo um SKU, que instalou um arquivo manifesto como parte de seu conteúdo para anunciar sua disponibilidade para extensões. O `<InstallationTarget>` elemento tem os seguintes atributos quando o atributo `Scope` tem o valor explícito ou padrão "ProductExtension":

  - `Id`- Este atributo identifica o pacote.  O atributo segue a convenção namespace: Company.Product.Feature.Name. O `Id` atributo pode conter apenas caracteres alfanuméricos e é limitado a 100 caracteres. Valores esperados:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`- Este atributo especifica uma gama de versões com as versões mínimas e máximas suportadas deste SKU. Um pacote pode detalhar as versões dos SKUs que ele suporta. A notação de faixa de versão é [10.0 - 11.0], onde

    - [ - versão mínima, inclusive.

    - ] - versão máxima inclusiva.

    - ( - versão mínima exclusiva.

    - ) - versão máxima exclusiva.

    - Versão única # - apenas a versão especificada.

    > [!IMPORTANT]
    > A versão 2.0 do VSIX Schema foi introduzida no Visual Studio 2012. Para usar este esquema, você deve ter o Visual Studio 2012 ou posterior instalado na máquina e usar o VSIXInstaller.exe que faz parte desse produto. Você pode segmentar versões anteriores do Visual Studio com um Visual Studio 2012 ou posterior vsixinstaller, mas apenas usando as versões posteriores do instalador.

    Os números da versão do Visual Studio 2017 podem ser encontrados no [Visual Studio, números de compilação e datas de lançamento.](../install/visual-studio-build-numbers-and-release-dates.md)

    Ao expressar a versão para os lançamentos do Visual Studio 2017, a versão menor deve ser sempre **0**. Por exemplo, visual studio 2017 versão 15.3.26730.0 deve ser expresso como [15.0.26730.0,16.0). Isso só é necessário para o Visual Studio 2017 e números de versão posteriores.

  - `AnyAttribute*`- `<InstallationTarget>` O elemento permite um conjunto aberto de atributos que é exposto em tempo de execução como um dicionário de par de valor de nome.

### <a name="dependencies-element"></a>Elemento dependências
 Este elemento contém uma lista de dependências que este pacote declara. Se alguma dependência for especificada, esses pacotes (identificados por eles `Id`) devem ter sido instalados antes.

- `<Dependency>`elemento - Este elemento filho tem os seguintes atributos:

  - `Id`- Este atributo deve ser um ID único para o pacote dependente. Esse valor de `<Metadata><Identity>Id` identidade deve corresponder ao atributo de um pacote do que este pacote depende. O `Id` atributo segue a convenção namespace: Company.Product.Feature.Name. O atributo pode conter apenas caracteres alfanuméricos e é limitado a 100 caracteres.

  - `Version`- Este atributo especifica uma gama de versões com as versões mínimas e máximas suportadas deste SKU. Um pacote pode detalhar as versões dos SKUs que ele suporta. A notação de faixa de versão é [12.0, 13.0], onde:

    - [ - versão mínima, inclusive.

    - ] - versão máxima inclusiva.

    - ( - versão mínima exclusiva.

    - ) - versão máxima exclusiva.

    - Versão única # - apenas a versão especificada.

  - `DisplayName`- Este atributo é o nome de exibição do pacote dependente, que é usado em elementos de IA, como caixas de diálogo e mensagens de erro. O atributo é opcional, a menos que o pacote dependente seja instalado pelo MSI.

  - `Location`- Este atributo opcional especifica o caminho relativo dentro deste VSIX para um pacote VSIX aninhado ou uma URL para o local de download para a dependência. Este atributo é usado para ajudar o usuário a localizar o pacote de pré-requisitos.

  - `AnyAttribute*`- `Dependency` O elemento aceita um conjunto aberto de atributos que serão expostos em tempo de execução como um dicionário de par de valor de nome.

### <a name="assets-element"></a>Elemento de ativos
 Este elemento contém `<Asset>` uma lista de tags para cada extensão ou elemento de conteúdo superfície por este pacote.

- `<Asset>`- Este elemento contém os seguintes atributos e elementos:

  - `Type`- Tipo de extensão ou conteúdo representado por este elemento. Cada `<Asset>` elemento deve `Type`ter um `<Asset>` único, mas `Type`vários elementos podem ter o mesmo . Este atributo deve ser representado como um nome totalmente qualificado, de acordo com as convenções de namespace. Os tipos conhecidos são:

    1. Microsoft.VisualStudio.vsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Modelo microsoft.visualstudio.project

    6. Modelo microsoft.visualstudio.item

    7. Microsoft.VisualStudio.Assembly

       Você pode criar seus próprios tipos e dar-lhes nomes únicos. Em tempo de execução dentro do Visual Studio, seu código pode enumerar e acessar esses tipos personalizados através da API do Extension Manager.

  - `Path`- o caminho relativo para o arquivo ou pasta dentro do pacote que contém o ativo.

  - `TargetVersion`- a faixa de versão à qual o ativo dado se aplica. Usado para enviar várias versões de ativos para diferentes versões do Visual Studio. Requer visual studio 2017.3 ou mais novo para ter efeito.

  - `AnyAttribute*`- Um conjunto aberto de atributos que é exposto em tempo de execução como um dicionário de par de valor de nome.

    `<AnyElement>*`- Qualquer conteúdo estruturado `<Asset>` é permitido entre uma tag start e end. Todos os elementos são expostos como uma lista de objetos XmlElement. As extensões VSIX podem definir metadados estruturados específicos do tipo no arquivo manifesto e enumera-los em tempo de execução.

### <a name="sample-manifest"></a>Manifesto amostral

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Confira também

- [Extensões do Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

---
title: Noções básicas do instalador de janelas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703415"
---
# <a name="windows-installer-basics"></a>Noções básicas do Windows Installer
O Windows Installer instala e desinstala aplicativos ou produtos de software no computador de um usuário, realizando essas tarefas em unidades chamadas componentes do Windows Installer (às vezes chamados de WICs ou apenas componentes). Um GUID identifica cada WIC, que é a unidade básica de instalação e contagem de referência para configurações usando o Windows Installer.

 Para obter uma documentação completa do Instalador do Windows, consulte o tópico SDK da plataforma, [O Instalador do Windows](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Autor de um VSPackage
 O Windows Installer usa pacotes de instalação, que contêm informações que o Windows Installer precisa para instalar, desinstalar ou reparar um produto e executar a interface do usuário de configuração (UI). Cada pacote de instalação inclui um arquivo .msi, que contém um banco de dados de instalação, um fluxo de informações de resumo e fluxos de dados para várias partes da instalação. Para usar o instalador, você deve escrever uma instalação. Como o instalador organiza instalações em torno do conceito de componentes e armazena informações sobre a instalação em um banco de dados relacional, o processo de autoria de um pacote de instalação implica amplamente as seguintes etapas:

1. Planeje sua autoria de configuração para apoiar suas estratégias de versionamento e lado a lado.

2. Identifique os recursos a serem apresentados aos usuários.

3. Organize o VSPackage e as dependências em componentes.

4. Preencha o banco de dados de instalação com informações.

5. Valide o pacote de instalação.

   Esta documentação está preocupada principalmente com a primeira e terceira etapas do processo. Durante essas etapas, você organiza seus recursos do VSPackage em WICs para que você [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]possa enquadrar sua estratégia de versionamento e manutenção para contabilizar as versões subseqüentes de . As três etapas restantes são cobertas detalhadamente na documentação do Windows Installer na plataforma SDK.

## <a name="key-terms"></a>Principais termos
 A seguir estão definições de termos-chave relacionados à tecnologia Do Instalador do Windows.

 Arquivos de recursos, chaves de registro, atalhos ou assim por diante que podem ser instalados em um computador. Esses recursos são agrupados logicamente nos componentes do Windows Installer.

 Componente do Instalador do Windows (WIC) A unidade básica de instalação representando um agrupamento lógico de recursos relacionados que são instalados e desinstalados como uma unidade. Os componentes do Windows Installer são identificados por um ID de componente exclusivo, ou GUID. Além disso, o Windows Installer mantém sua contagem de referência no nível WIC. Para flexibilidade máxima de versão, inclua não mais do que um recurso primário, como um DLL, em um determinado WIC. Observe que depois de identificar e preencher um WIC, dar-lhe um GUID e implantá-lo, você não poderá alterar sua composição. Para obter mais informações, consulte [Organizar aplicativos em Componentes](/windows/desktop/Msi/organizing-applications-into-components).

 Pacote (pacote Redist) Uma unidade de implantação que consiste em um arquivo .msi e arquivos de origem externos aos quais este arquivo pode apontar. Um pacote contém todas as informações que o Windows Installer precisa para executar a interface do usuário e instalar ou desinstalar o aplicativo.

 Arquivo .msi Um arquivo de armazenamento estruturado em COM contendo as instruções e os dados necessários para instalar um aplicativo. Cada pacote contém pelo menos um arquivo .msi. O arquivo .msi contém o banco de dados do instalador, um fluxo de informações de resumo e, possivelmente, uma ou mais transformações e arquivos de origem interna. Os arquivos a serem instalados podem ser compactados em um gabinete e armazenados em um fluxo no arquivo .msi ou armazenados, compactados ou descompactados, fora do arquivo .msi no meio de origem. Para obter mais informações, consulte [extensões de arquivo do instalador do Windows](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Aplicação das regras do instalador do Windows
 Dois conjuntos de regras determinam a implantação de recursos através dos componentes da sua configuração. Um conjunto de regras é mantido pelo próprio Instalador do Windows, enquanto você deve impor o segundo conjunto como autor da instalação.

> [!NOTE]
> A aplicação das regras do Windows Installer só ocorre se você executar uma validação do seu arquivo .msi. No entanto, você é advertido a tratar essas regras como melhores práticas. Para obter mais informações, consulte [Validando um banco de dados de instalação](/windows/desktop/Msi/validating-an-installation-database) e validação de [pacotes](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Regras impostas pelo instalador

- Todos os arquivos em um determinado componente devem ser instalados no mesmo diretório. Por outro lado, os arquivos instalados em pastas separadas devem pertencer a componentes separados.

- Só pode haver um caminho-chave por componente. O caminho-chave é simplesmente uma chave de arquivo ou registro que representa todo o componente.

#### <a name="component-provider-responsibilities"></a>Responsabilidades do provedor de componentes

- Quaisquer dois recursos que possam ser enviados separadamente em versões subseqüentes devem existir em componentes separados. Os recursos devem ser agrupados no mesmo componente apenas quando você tiver certeza de que esses recursos nunca serão enviados separadamente. Na verdade, recomenda-se que todos os recursos primários (DLLs, por exemplo) sempre existam em WICs separados. Para obter mais informações, consulte [Definindo componentes do instalador](/windows/desktop/Msi/defining-installer-components).

- Nenhum recurso com versão deve ser enviado em mais de um WIC.

## <a name="see-also"></a>Confira também
- [O que acontece se as regras do componente forem quebradas?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)

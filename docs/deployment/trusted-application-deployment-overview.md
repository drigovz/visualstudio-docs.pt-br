---
title: Visão geral da implantação de aplicativo confiável | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b3fca6db978eefc5af751d793ad299d89688cba
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806834"
---
# <a name="trusted-application-deployment-overview"></a>Visão geral da implantação de aplicativos confiáveis
Este tópico fornece uma visão geral de como implantar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos que têm permissões elevadas usando a tecnologia de implantação de aplicativo confiável.

 A implantação de aplicativos confiáveis, parte da tecnologia de implantação de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], torna mais fácil para as organizações de qualquer tamanho conceder permissões adicionais a um aplicativo gerenciado de maneira mais segura e segura sem a solicitação do usuário. Com a implantação de aplicativos confiáveis, uma organização pode apenas configurar um computador cliente para ter uma lista de editores confiáveis, que são identificados usando certificados Authenticode. Depois disso, qualquer aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] assinado por um desses editores confiáveis recebe um nível mais alto de confiança.

> [!NOTE]
> A implantação de aplicativo confiável requer uma configuração única do computador de um usuário. Em ambientes de desktop gerenciados, essa configuração pode ser executada usando a política global. Se isso não for o que você deseja para seu aplicativo, use a elevação de permissão em vez disso. Para obter mais informações, consulte [Securing ClickOnce Applications](../deployment/securing-clickonce-applications.md) (Protegendo aplicativos ClickOnce).

## <a name="trusted-application-deployment-basics"></a>Noções básicas de implantação de aplicativos confiáveis
 A tabela a seguir mostra os objetos e funções que estão envolvidos na implantação de aplicativo confiável.

|Objeto ou função|Descrição|
|--------------------|-----------------|
|administrador|A entidade organizacional responsável por atualizar e manter computadores cliente|
|Gerenciador de confiança|O subsistema dentro do Common Language Runtime (CLR) responsável por impor a segurança do aplicativo cliente.|
|editor|A entidade que grava e mantém o aplicativo.|
|implantador|A entidade que empacota e distribui o aplicativo aos usuários.|
|certificado|Uma assinatura criptográfica que consiste em uma chave pública e privada; geralmente emitido por uma autoridade de certificação (CA) que pode comprovar sua autenticidade.|
|Certificado Authenticode|Um certificado com metadados inseridos que descrevem, entre outras coisas, os usos para os quais o certificado pode ser empregado.|
|autoridade de certificação|Uma organização que verifica a identidade dos publicadores e emite os certificados inseridos com os metadados do editor.|
|autoridade raiz|Uma autoridade de certificação que autoriza outras autoridades de certificação a emitir certificados.|
|contêiner de chave|Um espaço de armazenamento lógico no Microsoft Windows para armazenar certificados.|
|fornecedor confiável|Um Publicador cujo certificado Authenticode foi adicionado a uma CTL (lista de certificados confiáveis) em um computador cliente.|

 Em organizações maiores, o Publicador e o implantador são frequentemente duas entidades separadas:

- O Publicador é o grupo que cria o aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

- O implantador é o grupo, normalmente o departamento de tecnologia da informação (TI), que distribui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para computadores empresariais corporativas.

Você deve seguir estas etapas para aproveitar a implantação de aplicativos confiáveis:

1. Obtenha um certificado para o Publicador.

2. Adicione o Publicador ao repositório de editores confiáveis em todos os clientes.

3. Crie seu aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

4. Assine o manifesto de implantação com o certificado do Publicador.

5. Publique a implantação do aplicativo em computadores cliente.

### <a name="obtain-a-certificate-for-the-publisher"></a>Obter um certificado para o Publicador
 Os certificados digitais são um componente fundamental do sistema de autenticação e segurança do Microsoft Authenticode. O Authenticode é uma parte padrão do sistema operacional Windows. Todos os aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] devem ser assinados com um certificado digital, independentemente de participarem de uma implantação de aplicativo confiável. Para obter uma explicação completa de como o Authenticode funciona com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).

### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Adicionar o Publicador à loja de editores confiáveis
 Para que seu aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] receba um nível mais alto de confiança, você deve adicionar seu certificado como um editor confiável para cada computador cliente no qual o aplicativo será executado. A execução dessa tarefa é uma configuração única. Após a conclusão, você pode implantar quantos aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] assinados com o certificado do Publicador como desejar e todos eles serão executados com alta confiança.

 Se você estiver implantando seu aplicativo em um ambiente de área de trabalho gerenciada; por exemplo, uma intranet corporativa que executa o sistema operacional Windows; Você pode adicionar editores confiáveis ao armazenamento de um cliente criando uma nova lista de certificados confiáveis (CTL) com Política de Grupo. Para obter mais informações, consulte [criar uma lista de certificados confiáveis para um objeto política de grupo](/previous-versions/windows/it-pro/windows-server-2003/cc728449(v=ws.10)).

 Se você não estiver implantando seu aplicativo em um ambiente de área de trabalho gerenciada, você tem as seguintes opções para adicionar um certificado ao repositório de fornecedores confiáveis:

- O namespace <xref:System.Security.Cryptography?displayProperty=fullName>.

- *Certmgr. exe*, que é um componente do Internet Explorer e, portanto, existe no Windows 98 e em todas as versões posteriores. Para obter mais informações, consulte [certmgr. exe (ferramenta do Gerenciador de certificados)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).

### <a name="create-a-clickonce-application"></a>Criar um aplicativo ClickOnce
 Um aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é um aplicativo cliente .NET Framework combinado com arquivos de manifesto que descrevem os parâmetros de instalação do aplicativo e de fornecimento. Você pode transformar seu programa em um aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando o comando **publicar** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como alternativa, você pode gerar todos os arquivos necessários para a implantação de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando as ferramentas incluídas no [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obter etapas detalhadas sobre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, consulte [passo a passo: Como implantar manualmente aplicativos ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

 A implantação de aplicativos confiáveis é específica para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]e só pode ser usada com aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

### <a name="sign-the-deployment"></a>Assinar a implantação
 Depois de obter o certificado, você deve usá-lo para assinar sua implantação. Se você estiver implantando seu aplicativo usando o assistente de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Publish, o assistente gerará automaticamente um certificado de teste para você se você não tiver especificado um certificado por conta própria. Você também pode usar a janela designer de projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no entanto, para fornecer um certificado fornecido por uma autoridade de certificação.  Consulte também [como publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!CAUTION]
> Não recomendamos que o aplicativo seja implantado com um certificado de teste.

 Você também pode assinar o aplicativo usando as ferramentas do SDK do *Mage. exe* ou *MageUI. exe* . Para obter mais informações, consulte [Walkthrough: implantar manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Para obter uma lista completa das opções de linha de comando relacionadas à assinatura de implantação, consulte [Mage. exe (manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

### <a name="publish-the-application"></a>Publicar o aplicativo
 Assim que você assinar seus manifestos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], o aplicativo estará pronto para ser publicado no local de instalação. O local de instalação pode ser um servidor Web, um compartilhamento de arquivos ou o disco local. Quando um cliente acessa o manifesto de implantação pela primeira vez, o Gerenciador de confiança deve escolher se o aplicativo de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] recebeu autoridade ou não para ser executado em um nível mais alto de confiança por um fornecedor confiável instalado. O Gerenciador de confiança faz essa escolha comparando o certificado usado para assinar a implantação com os certificados armazenados no repositório de fornecedores confiáveis do cliente. Se o Gerenciador de confiança encontrar uma correspondência, o aplicativo será executado com confiança alta.

## <a name="trusted-application-deployment-and-permission-elevation"></a>Implantação de aplicativo confiável e elevação de permissão
 Se o Publicador atual não for um editor confiável, o Gerenciador de confiança usará a elevação de permissão para consultar o usuário sobre se ele deseja conceder permissões elevadas ao seu aplicativo. No entanto, se a elevação de permissões for desabilitada pelo administrador, o aplicativo não poderá obter permissão para executar. O aplicativo não será executado e nenhuma notificação será exibida ao usuário. Para obter mais informações sobre elevação de permissões, consulte [Securing ClickOnce Applications](../deployment/securing-clickonce-applications.md).

## <a name="limitations-of-trusted-application-deployment"></a>Limitações da implantação de aplicativos confiáveis
 Você pode usar a implantação de aplicativo confiável para conceder confiança elevada a aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantados pela Web ou por meio de um compartilhamento de arquivos corporativo. Você não precisa usar a implantação de aplicativos confiáveis para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos distribuídos em um CD, porque, por padrão, esses aplicativos recebem confiança total.

## <a name="see-also"></a>Consulte também
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Passo a passo: implantar um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

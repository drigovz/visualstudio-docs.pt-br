---
title: Proteger soluções do Office
description: Saiba como o modelo de segurança para soluções do Office envolve várias tecnologias, incluindo o Ferramentas do Visual Studio para o tempo de execução do Office e o ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bedb49a6d5d17e3c9f79a652183c2b4cd748ff6c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528485"
---
# <a name="secure-office-solutions"></a>Proteger soluções do Office
  O modelo de segurança para soluções do Office envolve várias tecnologias: o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , a central de confiabilidade em Microsoft Office e a zona de sites restritos do Internet Explorer. As seções a seguir descrevem como os diferentes recursos de segurança funcionam:

- [Conceder confiança às soluções do Office](#GrantingTrustToSolutions)

- [Conceder confiança aos documentos](#GrantingTrustToDocuments)

- [Conceder confiança ao usar Windows Installer](#GrantingTrustWindowsInstaller)

- [Considerações de segurança específicas para soluções do Office](#Security)

- [Segurança durante o desenvolvimento](#SecurityDuringDeployment)

- [Visual Studio Tools para Office Runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Conceder confiança às soluções do Office
 A concessão de confiança às soluções do Office significa modificar a política de segurança de cada usuário final para confiar na solução do Office com base nas seguintes evidências:

- O certificado usado para assinar o manifesto de implantação.

- A URL do manifesto de implantação.

  Para obter mais informações, consulte [Grant Trust to Office Solutions](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Conceder confiança aos documentos
 Uma personalização no nível do documento requer que o documento esteja em um diretório designado como um local confiável. Para obter mais informações, consulte [Grant Trust to Documents](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Conceder confiança ao usar Windows Installer
 Você pode usar Windows Installer para criar um arquivo MSI para instalar soluções do Office no diretório arquivos de programas, o que exige direitos de administrador. Para soluções do Office no diretório arquivos de programas, o tempo de execução do Visual Studio 2010 Tools for Office considera essas soluções do Office como confiáveis e não mostra o prompt de confiança do ClickOnce.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Considerações de segurança específicas para soluções do Office
 Os recursos de segurança fornecidos pelo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e o Microsoft Office podem ajudar a proteger contra uma variedade de possíveis ameaças de segurança nas soluções do Office. Para obter mais informações, consulte [considerações de segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Segurança durante o desenvolvimento
 Para facilitar o processo de desenvolvimento, o Visual Studio define a política de segurança necessária para executar e depurar sua solução no seu computador toda vez que você criar um projeto. Em alguns cenários, talvez seja necessário tomar etapas de segurança adicionais para desenvolver o projeto.

### <a name="document-level-solutions"></a>Soluções de nível de documento
 O caminho totalmente qualificado de um documento deve ser adicionado à lista de locais confiáveis no aplicativo Microsoft Office se você estiver desenvolvendo os seguintes tipos de projetos:

- Soluções de nível de documento que estão em um compartilhamento de arquivos de rede, como *\\ \Servername\Sharename*.

- Soluções de nível de documento para o Word que usam arquivos *. doc* ou *. docm* .

  Inclua os subdiretórios ao adicionar o local do documento à lista de locais confiáveis ou inclua especificamente as pastas Debug e Build. Para obter mais informações, consulte o artigo de ajuda online do Microsoft Office [criar, remover ou alterar um local confiável para seus arquivos](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Certificados temporários
 O Visual Studio criará um certificado temporário se um certificado de autenticação ainda não existir. Você deve usar esse certificado temporário somente durante o desenvolvimento e comprar um certificado oficial para implantação.

 O certificado temporário é gerado depois que um projeto do Office é criado pela primeira vez. Na próxima vez que você pressionar **F5**, o projeto será recriado porque o projeto será marcado como alterado quando o certificado for adicionado.

 Pode haver muitos certificados temporários após um tempo, portanto, você deve limpar os certificados temporários ocasionalmente.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Ferramentas do Visual Studio para o tempo de execução do Office
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tem recursos para verificar a identidade do Publicador e as permissões que são concedidas a uma personalização. Ele verifica essas permissões por meio de uma sequência de verificações de segurança.

### <a name="security-during-customization-loading"></a>Segurança durante o carregamento da personalização
 Quando uma personalização no nível do documento é carregada, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sempre verifica se o documento está na lista de locais confiáveis. Além disso, o tempo de execução verifica se a solução solicita FullTrust no manifesto do aplicativo. Ele não executa nenhuma verificação de segurança adicional enquanto a personalização está sendo carregada.

### <a name="sequence-of-security-checks-during-installation"></a>Sequência de verificações de segurança durante a instalação
 Quando uma solução do Office é instalada ou atualizada, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] executa um conjunto de verificações de segurança em uma sequência específica para tomar uma decisão de confiança. Uma solução será instalada ou atualizada somente se o tempo de execução determinar que a solução é confiável.

 Você pode iniciar o processo de instalação de uma das quatro maneiras: executando o programa de instalação, abrindo o manifesto de implantação, abrindo o host de aplicativo Microsoft Office ou executando *VSTOInstaller.exe*.

 A primeira verificação de segurança aplica-se somente a soluções de nível de documento. O documento de uma solução em nível de documento deve estar em um local confiável. Se o documento estiver em um compartilhamento de arquivos de rede remota ou tiver uma extensão de nome de arquivo *. doc* ou *. docm* , o local do documento deverá ser adicionado à lista de locais confiáveis. Para obter mais informações, consulte [Grant Trust to Documents](../vsto/granting-trust-to-documents.md).

 ![Segurança do VSTO – instalando do Microsoft Office](../vsto/media/host-install.png "Segurança do VSTO – instalando do Microsoft Office")

 O próximo conjunto de verificações de segurança é do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ClickOnce. Para passar essas verificações, as soluções do Office devem solicitar permissões FullTrust, ser assinadas com um certificado que não esteja listado na lista de Publicador não confiável e estar em um local que não esteja na zona restrita do Internet Explorer. Se o certificado estiver na lista de editores confiáveis, a solução será instalada imediatamente. Caso contrário, se não houvesse falha em uma das verificações, a solução continuará no conjunto final de verificações.

 ![Segurança do VSTO para instalar soluções](../vsto/media/installing.png "Segurança do VSTO para instalar soluções")

 Se a [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] solicitação de confiança for permitida e a solução ainda não tiver recebido confiança, o tempo de execução permitirá que a decisão de confiança seja feita pelo usuário final. Se o usuário conceder confiança à solução, uma entrada será adicionada à lista de inclusão do usuário. Todas as soluções na lista de inclusão do usuário têm confiança total e podem ser instaladas e executadas.

 A partir do Visual Studio 2010, a lista de inclusão será ignorada se a solução do Office for instalada usando Windows Installer (MSI) no diretório arquivos de programas. Para obter mais informações, consulte [confiar em soluções do Office usando listas de inclusão](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Segurança do VSTO-usando o programa de instalação para instalar o](../vsto/media/setup-vstoinstaller.png "Segurança do VSTO-usando o programa de instalação para instalar o")

## <a name="see-also"></a>Veja também

- [Conceder confiança às soluções do Office](../vsto/granting-trust-to-office-solutions.md)
- [Conceder confiança aos documentos](../vsto/granting-trust-to-documents.md)
- [Confiar em soluções do Office usando listas de inclusão](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Como: configurar a segurança da lista de inclusão](../vsto/how-to-configure-inclusion-list-security.md)
- [Como: assinar soluções do Office](../vsto/how-to-sign-office-solutions.md)
- [Solucionar problemas de segurança da solução do Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Referência do ClickOnce](../deployment/clickonce-reference.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)

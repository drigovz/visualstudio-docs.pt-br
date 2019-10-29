---
title: Confiar em soluções do Office usando listas de inclusão
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4787831be31e2f91d668d4e3e7ca91496d7595a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985541"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Confiar em soluções do Office usando listas de inclusão
  As listas de inclusão permitem que os usuários conceda confiança às soluções do Office que são assinadas com um certificado que identifica o Publicador. As listas de inclusão são específicas do usuário e podem ser usadas para personalizações em nível de documento e suplementos do VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Quando um usuário inicia uma solução do Office que não recebeu confiança para esse usuário, a solução de Microsoft Office solicita a ele uma decisão de segurança com um prompt de confiança de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Se o usuário decidir confiar na solução, a personalização será executada e o usuário não será solicitado na próxima vez.

## <a name="inclusion-list-and-windows-installer"></a>Lista de inclusão e Windows Installer
 A instalação das soluções do Office no diretório *arquivos de programas* usando Windows Installer requer direitos de administrador. Para soluções do Office no diretório *arquivos de programas* , o ferramentas do Visual Studio para o tempo de execução do Office não verifica mais a lista de inclusão porque as soluções do Office já receberam permissão FullTrust.

## <a name="clickonce-trust-prompt"></a>Prompt de confiança do ClickOnce
 Usando a implementação de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] para soluções do Office, os administradores podem configurar o nível de prompt de confiança para permitir a solicitação, desabilitar a solicitação ou exigir um certificado confiável. Essa configuração é feita usando uma chave do registro que controla o acesso à lista de inclusão.

 Se a solicitação estiver desabilitada, somente as soluções que têm um certificado confiável e conhecido poderão ser instaladas. Se o nível de solicitação for definido como Authenticode necessário, a solução deverá ser assinada com um certificado de uma autoridade conhecida, mas não exigirá um certificado que se encadeia a uma autoridade raiz confiável (um certificado confiável). Se a solicitação for permitida, a solução poderá ser assinada com um certificado com uma identidade desconhecida. Nesse cenário, a decisão de confiança é adiada para o usuário final e um certificado temporário seria suficiente para instalar uma solução.

 Para obter mais informações, consulte [como: configurar segurança da lista de inclusão](../vsto/how-to-configure-inclusion-list-security.md) e tabela 2, intitulada efeitos de inicialização do valor da chave do registro de nível de solicitação, em [Configurar Publicadores confiáveis do ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Estrutura da lista de inclusão
 Uma entrada de lista de inclusão válida tem duas partes: um caminho para o manifesto de implantação e a chave pública usada para assinar a solução. Depois que uma solução é adicionada à lista de inclusão, ela é considerada confiável. Quando a solução do Office é executada, o aplicativo do Office compara a chave pública na lista de inclusão com a chave de assinatura no manifesto de implantação para verificar se a solução que está em execução no momento é a mesma que a versão confiável original.

## <a name="see-also"></a>Consulte também
- [Conceder confiança às soluções do Office](../vsto/granting-trust-to-office-solutions.md)
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)

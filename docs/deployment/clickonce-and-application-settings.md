---
title: ClickOnce e configurações de aplicativo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153df515fc762b7262dce81d8c1d1c4fe617ad61
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608416"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce e as configurações de aplicativo
Configurações de aplicativo para Windows Forms torna mais fácil criar, armazenar e manter aplicativos personalizados e preferências do usuário no cliente. Este documento descreve como os arquivos de configurações do aplicativo funcionam em um aplicativo ClickOnce e como o ClickOnce migra as configurações quando o usuário é atualizado para a próxima versão.

 As informações a seguir se aplica somente ao provedor de configurações do aplicativo padrão, o \<xref:System.Configuration.LocalFileSettingsProvider > classe. Se você fornecer um provedor personalizado, esse provedor determinará como ela armazena seus dados e como ele é atualizado suas configurações entre versões. Para obter mais informações sobre provedores de configurações do aplicativo, consulte [arquitetura de configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Arquivos de configurações do aplicativo
 Configurações do aplicativo consome dois arquivos:  *\<aplicativo >. exe* e *User*, onde *aplicativo* é o nome do seu aplicativo de formulários do Windows. *User* é criado na hora do cliente pela primeira seu aplicativo armazena configurações no escopo do usuário. *\<aplicativo >. exe*, por outro lado, continuará a existir antes da implantação se você definir valores padrão para configurações. Visual Studio incluirá esse arquivo automaticamente quando você usa seu **publicar** comando. Se você criar seu aplicativo ClickOnce usando *Mage.exe* ou *MageUI.exe*, verifique se esse arquivo é incluído com outros arquivos do seu aplicativo ao popular o manifesto do aplicativo.

 Em aplicativos Windows Forms não implantado usando o ClickOnce, um aplicativo  *\<aplicativo >. exe* arquivo é armazenado no diretório do aplicativo, enquanto o *User* arquivo está armazenado o usuário **Documents and Settings** pasta. Em um aplicativo do ClickOnce  *\<aplicativo >. exe* reside no diretório do aplicativo dentro do cache do aplicativo ClickOnce, e *User* reside no diretório de dados do ClickOnce para o aplicativo.

 Independentemente de como você implanta seu aplicativo, as configurações de aplicativo garante seguro acesso de leitura  *\<aplicativo >. exe*e o acesso de leitura/gravação seguro para *User*.

 Em um aplicativo ClickOnce, o tamanho dos arquivos de configuração usado pelas configurações de aplicativo é restrito pelo tamanho do cache do ClickOnce. Para obter mais informações, consulte [visão geral de cache do ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Atualizações de versão
 Assim como cada versão de um aplicativo ClickOnce é isolada de todas as outras versões, as configurações do aplicativo para um aplicativo ClickOnce são isoladas das configurações para outras versões também. Quando o usuário é atualizado para uma versão posterior do seu aplicativo, as configurações do aplicativo compara as configurações de versão mais recente (número mais alto) contra as configurações fornecidas com a versão atualizada e os mescla as configurações em um novo conjunto de arquivos de configurações.

 A tabela a seguir descreve como as configurações do aplicativo decide quais configurações para copiar.

|Tipo de alteração|Ação de atualização|
|--------------------|--------------------|
|Configuração adicionada ao  *\<aplicativo >. exe*|A nova configuração será mesclada na versão atual  *\<aplicativo >. exe*|
|Configuração retirada  *\<aplicativo >. exe*|A configuração antiga é removida da versão atual  *\<aplicativo >. exe*|
|Padrão da configuração alterada; configuração local ainda é definida como padrão original no *User*|A configuração será mesclada na versão atual *User* com o novo padrão como o valor|
|Padrão da configuração alterada; configuração de conjunto não padrão em *User*|A configuração será mesclada na versão atual *User* com o valor não padrão retido|

Se você tiver criado suas próprias configurações de aplicativo a classe de wrapper e deseja personalizar a lógica de atualização, você pode substituir o \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A > método.

## <a name="clickonce-and-roaming-settings"></a>ClickOnce e configurações de roaming
 ClickOnce não funciona com as configurações de roaming, que permite que seu arquivo de configurações a seguir você entre computadores em uma rede. Se você precisar de configurações de roaming, será necessário implementar um provedor de configurações do aplicativo que armazena as configurações de rede ou desenvolver suas próprias classes de configurações personalizadas para armazenar as configurações em um computador remoto. Para obter mais informações em provedores de configurações, consulte [arquitetura de configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Consulte também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Visão geral das configurações de aplicativo](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Visão geral do cache do ClickOnce](../deployment/clickonce-cache-overview.md)
- [Acesso a dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
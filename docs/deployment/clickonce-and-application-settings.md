---
title: Configurações do ClickOnce e do aplicativo | Microsoft Docs
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
ms.openlocfilehash: a72b5bc3f3645d9af1008f2c178ab285e8b45449
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184127"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce e as configurações de aplicativo
As configurações do aplicativo para Windows Forms facilita a criação, o armazenamento e a manutenção de preferências personalizadas do aplicativo e do usuário no cliente. O documento a seguir descreve como os arquivos de configurações de aplicativo funcionam em um aplicativo ClickOnce e como o ClickOnce migra as configurações quando o usuário atualiza para a próxima versão.

 As informações a seguir se aplicam somente ao provedor de configurações de aplicativo padrão, a <xref:System.Configuration.LocalFileSettingsProvider> classe. Se você fornecer um provedor personalizado, esse provedor determinará como ele armazena seus dados e como ele atualiza suas configurações entre versões. Para obter mais informações sobre provedores de configurações do aplicativo, consulte [arquitetura de configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Arquivos de configurações do aplicativo
 As configurações do aplicativo consomem dois arquivos: * \<app>.exe.config* e *user.config*, em que *app* é o nome do seu aplicativo Windows Forms. *user.config* é criado no cliente na primeira vez em que o aplicativo armazena configurações no escopo do usuário. * \<app>.exe.config*, por outro lado, existirá antes da implantação se você definir valores padrão para as configurações. O Visual Studio incluirá esse arquivo automaticamente quando você usar o comando **Publish** . Se você criar seu aplicativo ClickOnce usando *Mage.exe* ou *MageUI.exe*, deverá verificar se esse arquivo está incluído nos outros arquivos do seu aplicativo ao preencher o manifesto do aplicativo.

 Em um aplicativo Windows Forms não implantado usando o ClickOnce, o arquivo de * \<app>.exe.config* de um aplicativo é armazenado no diretório do aplicativo, enquanto o arquivo de *user.config* é armazenado na pasta **Documents and Settings** do usuário. Em um aplicativo ClickOnce, * \<app>.exe.config* reside no diretório do aplicativo dentro do cache do aplicativo ClickOnce e *user.config* reside no diretório de dados do ClickOnce para esse aplicativo.

 Independentemente de como você implanta seu aplicativo, as configurações do aplicativo garantem acesso seguro de leitura para * \<app>.exe.config*e acesso de leitura/gravação seguro para *user.config*.

 Em um aplicativo ClickOnce, o tamanho dos arquivos de configuração usados pelas configurações do aplicativo é restrito pelo tamanho do cache do ClickOnce. Para obter mais informações, consulte [visão geral do cache do ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Atualizações de versão
 Assim como cada versão de um aplicativo ClickOnce é isolada de todas as outras versões, as configurações de aplicativo para um aplicativo ClickOnce também são isoladas das configurações para outras versões. Quando o usuário atualiza para uma versão posterior do seu aplicativo, as configurações do aplicativo comparam as configurações da versão mais recente (mais alta) em relação às configurações fornecidas com a versão atualizada e mesclam as configurações em um novo conjunto de arquivos de configurações.

 A tabela a seguir descreve como as configurações de aplicativo decidem quais configurações copiar.

|Tipo de alteração|Ação de atualização|
|--------------------|--------------------|
|Configuração adicionada a * \<app>.exe.config*|A nova configuração é mesclada com a * \<app>.exe.config* da versão atual|
|Configuração removida do * \<app>.exe.config*|A configuração antiga é removida da * \<app>.exe.config* da versão atual|
|O padrão da configuração foi alterado; configuração local ainda definida como padrão original no *user.config*|A configuração é mesclada com o *user.config* da versão atual com o novo padrão como o valor|
|O padrão da configuração foi alterado; configuração definida como não padrão no *user.config*|A configuração é mesclada com o *user.config* da versão atual com o valor não padrão mantido|

Se você criou sua própria classe wrapper de configurações de aplicativo e deseja personalizar a lógica de atualização, você pode substituir o <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> método.

## <a name="clickonce-and-roaming-settings"></a>Configurações de roaming e ClickOnce
 O ClickOnce não funciona com configurações de roaming, o que permite que o arquivo de configurações o acompanhe entre computadores em uma rede. Se você precisar de configurações de roaming, será necessário implementar um provedor de configurações de aplicativo que armazene as configurações pela rede ou desenvolver suas próprias classes de configurações personalizadas para armazenar as configurações em um computador remoto. Para obter mais informações em provedores de configurações, consulte [arquitetura de configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Confira também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Visão geral das configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Visão geral do cache do ClickOnce](../deployment/clickonce-cache-overview.md)
- [Acesso a dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
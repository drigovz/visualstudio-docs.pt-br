---
title: Detectando requisitos do sistema | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708728"
---
# <a name="detect-system-requirements"></a>Detectar os requisitos do sistema
Um VSPackage não pode funcionar a menos que o Visual Studio esteja instalado. Quando você usa o Microsoft Windows Installer para gerenciar a instalação do seu VSPackage, você pode configurar o instalador para detectar se o Visual Studio está instalado. Você também pode configurá-lo para verificar o sistema para outros requisitos, por exemplo, uma versão específica do Windows ou uma quantidade particular de RAM.

## <a name="detect-visual-studio-editions"></a>Detecte edições do Visual Studio
 Para determinar se uma edição do Visual Studio está instalada, verifique se o valor da chave de registro **instalar** é *(REG_DWORD) 1* na pasta apropriada, conforme listado na tabela a seguir. Observe que há uma hierarquia de edições do Visual Studio:

1. Enterprise

2. Professional

3. Comunidade

Quando uma edição mais nova é instalada, as chaves de registro dessa edição são adicionadas, bem como para edições anteriores. Ou seja, se a edição Enterprise for instalada, a tecla **Install** será definida como *1* para a Enterprise, bem como para as edições Profissional e Comunitária. Portanto, você precisa verificar apenas para a edição mais recente que você precisa.

> [!NOTE]
> Na versão de 64 bits do editor de registro, as teclas de 32 bits são exibidas em **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. As teclas do Visual Studio estão sob **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Serviço\\**.

|Produto|Chave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Serviço\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Serviço\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Serviço\14.0\comunidade|
|Visual Studio 2015 Shell (integrado e isolado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Serviço\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Detecte quando o Visual Studio estiver em execução
 Seu VSPackage não pode ser registrado corretamente se o Visual Studio estiver sendo executado quando o VSPackage estiver instalado. O instalador deve detectar quando o Visual Studio estiver em execução e, em seguida, recusar-se a instalar o programa. O Windows Installer não permite que você use entradas de tabela para ativar tal detecção. Em vez disso, você deve criar uma `EnumProcesses` ação personalizada, da seguinte forma: Use a função para detectar o processo *devenv.exe* e, em seguida, defina uma propriedade do instalador que é usada em uma condição de lançamento ou exiba condicionalmente uma caixa de diálogo que solicita ao usuário que feche o Visual Studio.

## <a name="see-also"></a>Confira também
- [Instale pacotes VS com o instalador do Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

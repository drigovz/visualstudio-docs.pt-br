---
title: Detectar os requisitos do sistema | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4232a057c97d3d457a60d97fa000090c18428f66
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050488"
---
# <a name="detect-system-requirements"></a>Detectar os requisitos do sistema
Um VSPackage não funcionará a menos que o Visual Studio está instalado. Quando você usa o Microsoft Windows Installer para gerenciar a instalação de seu VSPackage, você pode configurar o instalador para detectar se o Visual Studio está instalado. Você também pode configurá-lo para verificar o sistema para outros requisitos, por exemplo, uma versão específica do Windows ou uma determinada quantidade de RAM.

## <a name="detect-visual-studio-editions"></a>Detectar as edições do Visual Studio
 Para determinar se uma edição do Visual Studio está instalada, verifique se o valor da **instale** chave do registro está *(REG_DWORD) 1* na pasta apropriada, conforme listado na tabela a seguir. Observe que há uma hierarquia de edições do Visual Studio:

1. Enterprise

2. Professional

3. Comunidade

Quando uma edição mais recente está instalada, as chaves do registro para essa edição são adicionadas, bem como para as edições anteriores. Ou seja, se a Enterprise edition estiver instalada, o **instale** chave é definida como *1* para a empresa, bem como para as edições Professional e Community. Portanto, você precisará verificar apenas para a edição mais recente, que você precisa.

> [!NOTE]
>  Na versão de 64 bits do editor do registro, chaves de 32 bits são exibidas sob **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. As chaves do Visual Studio estão sob **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Produto|Chave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (integrado e isolado)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Detectar quando o Visual Studio está em execução
 O VSPackage não pode ser registrado corretamente se o Visual Studio está em execução quando o VSPackage é instalado. O instalador deve detectar quando o Visual Studio está em execução e, em seguida, se recusará a usar o programa. Windows Installer não permite que você use as entradas da tabela para habilitar essa detecção. Em vez disso, você deve criar uma ação personalizada, da seguinte maneira: Use o `EnumProcesses` função para detectar o *devenv.exe* processar e, em seguida, definir uma propriedade de instalador que é usada em uma condição de inicialização ou exibe condicionalmente uma caixa de diálogo que solicita que o usuário feche o Visual Studio.

## <a name="see-also"></a>Consulte também
- [Instalar VSPackages com o Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
---
title: Gestão de Componentes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709331"
---
# <a name="component-management"></a>Gerenciamento de componentes
As unidades de tarefas no Instalador do Windows são referidas como componentes do Instalador do Windows (às vezes chamados de WICs ou apenas componentes). Um GUID identifica cada WIC, que é a unidade básica de instalação e contagem de referência para configurações que usam o Windows Installer.

 Embora você possa usar vários produtos para criar o instalador VSPackage, essa discussão assume o uso de arquivos Windows Installer *(.msi).* Ao criar seu instalador, você deve gerenciar corretamente a implantação do arquivo para que a contagem correta de referência aconteça o tempo todo. Consequentemente, diferentes versões do seu produto não interferirão ou se quebrarão em uma mistura de cenários de instalação e desinstalação.

 No Windows Installer, a contagem de referência ocorre no nível do componente. Você deve organizar cuidadosamente seus recursos - arquivos, entradas de registro e assim por diante - em componentes. Existem outros níveis de organização — como módulos, recursos e produtos — que podem ajudar em diferentes cenários. Para obter mais informações, consulte [o básico do Windows Installer](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Diretrizes de configuração de autoria para instalação lado a lado

- Arquivos de autor e chaves de registro que são compartilhados entre versões em seus próprios componentes.

     Isso permite que você os consuma facilmente na próxima versão. Por exemplo, digite bibliotecas registradas globalmente, extensões de arquivo, outros itens registrados em **HKEY_CLASSES_ROOT**e assim por diante.

- Agrupar componentes compartilhados em módulos de mesclagem separados.

     Essa estratégia ajuda você a escrever corretamente para a instalação lado a lado avançando.

- Instale arquivos compartilhados e chaves de registro usando os mesmos componentes do Windows Installer em versões.

     Se você usar um componente diferente, arquivos e entradas de registro serão desinstalados quando um VSPackage versãodo é desinstalado, mas outro VSPackage ainda está instalado.

- Não misture itens com versões e compartilhados no mesmo componente.

     Isso torna impossível instalar itens compartilhados em um local global e itens versionados em locais isolados.

- Não tenha chaves de registro compartilhadas que apontam para arquivos com versões.

     Se você fizer isso, as chaves compartilhadas serão substituídas quando outro VSPackage versão do VS for instalado. Depois de remover a segunda versão, o arquivo para o qual a chave está apontando se foi.

## <a name="see-also"></a>Confira também
- [Escolha entre VSPackages compartilhados e versões](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Cenários de configuração do VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

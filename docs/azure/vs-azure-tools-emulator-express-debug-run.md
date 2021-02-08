---
title: Emulador Express para executar/depurar o serviço de nuvem do Azure localmente
ms.custom: SEO-VS-2020
description: Usando o Emulator Express para executar e depurar um serviço de nuvem em um computador local
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: 08381be4fdc4fc23b70fb252c653b62398799a30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844210"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Uso do Emulator Express para executar e depurar um serviço de nuvem do Azure em um computador local
Ao usar o Emulator Express, você poderá testar e depurar um serviço de nuvem sem executar o Visual Studio como um administrador. É possível definir as configurações do projeto para usar o Emulator Express ou o emulador completo, dependendo dos requisitos do seu serviço de nuvem. Para saber mais sobre o emulador completo, consulte [Executar um aplicativo Azure no emulador de computação](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Uso do Emulator Express no Visual Studio
Quando você cria um projeto n SDK 2.3 ou posterior do Azure, o Emulator Express é usado automaticamente. No caso de projetos existentes que foram criados com uma versão anterior do SDK do Azure, use as seguintes etapas para selecionar o Emulator Express:

1. Crie ou abra um projeto de serviço de nuvem do Azure no Visual Studio.

1. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e, no menu de contexto, selecione **Propriedades**.

1. Nas páginas de propriedades dos projetos, selecione a guia **Web**.

    ![Propriedades de um projeto de serviço de nuvem do Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. Em **Development Server Local**, escolha a opção **Usar o IIS Express**.

1. Em **Emulador**, selecione **Usar Emulator Express**.

1. Para iniciar o Emulator Express, execute o seguinte comando em um prompt de comando:

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Limitações do Emulator Express
Os seguintes problemas são limitações conhecidas do Emulator Express:

- O Emulator Express não é compatível com o Servidor Web do IIS.
- O serviço de nuvem pode conter várias funções, mas cada função é limitada a uma instância.
- Você não pode acessar números de porta abaixo de 1000. Se você usar um provedor de autenticação que normalmente usa uma porta abaixo de 1000, talvez seja necessário alterar esse valor para um número de porta acima de 1000.
- As limitações que se aplicam ao Emulador de Computação do Azure também se aplicam ao Emulator Express. Por exemplo, você não pode ter mais de 50 instâncias de função por implantação. Para saber mais sobre o Emulador de Computação do Azure, confira [Executar um aplicativo do Azure no Emulador de Computação](vs-azure-tools-performance-profiling-cloud-services.md).

## <a name="next-steps"></a>Próximas etapas
[Depurando serviços de nuvem do Azure](vs-azure-tools-debugging-cloud-services-overview.md)

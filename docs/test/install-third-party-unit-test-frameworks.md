---
title: Instalar estruturas de teste de unidade de terceiros
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9f61b52f72474a8ecd8fac4c30265dcd7cf36a5e
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857691"
---
# <a name="install-unit-test-frameworks"></a>Instalar estruturas de teste de unidade

O Gerenciador de Testes do Visual Studio pode executar testes de qualquer estrutura de teste de unidade que desenvolveu uma interface de adaptador para ele. A instalação da estrutura copia os binários e adiciona modelos de projeto do Visual Studio para os idiomas que ele dá suporte. Quando você cria um projeto com o modelo, a estrutura é registrada com o Gerenciador de Testes.

Uma solução do Visual Studio pode conter projetos de teste de unidade que usam diferentes estruturas e que são direcionados em diferentes idiomas.

O [MSTest](getting-started-with-unit-testing.md) é a estrutura de teste fornecida pelo Visual Studio e é instalada por padrão.

## <a name="acquire-frameworks"></a>Adquirir estruturas

Instalar estruturas de teste de unidade de terceiros usando o **Gerenciador de Pacotes do NuGet**.

1. Clique com o botão direito do mouse no projeto que conterá o código de teste e selecione **Gerenciar Pacotes do NuGet**.

2. No **Gerenciador de Pacotes do NuGet**, procure a estrutura de teste que você deseja instalar e, em seguida, clique em **Instalar**.

   ![Gerenciador de Pacotes do NuGet no Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Atualizar para os adaptadores de teste mais recentes

Atualização para o adaptador de teste estável mais recente para aproveitar melhor a detecção e a execução de teste. Para saber mais sobre atualizações para adaptadores de teste MSTest, NUnit e xUnit, veja o [blog do Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Para atualizar para a versão estável mais recente do adaptador de teste

1. Abra o Gerenciador de Pacotes Nuget da solução navegando até **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Gerenciar Pacotes NuGet da Solução**.

2. Clique na guia **Atualizações** e pesquise os adaptadores de teste do MSTest, NUnit ou xUnit que estão instalados.

3. Selecione cada adaptador de teste e, em seguida, selecione a última versão estável no menu suspenso.

4. Escolha o botão **Instalar**.

   ![Atualizar adaptador de teste](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Consulte também

- [Efetue testes de unidade em seu código](../test/unit-test-your-code.md)

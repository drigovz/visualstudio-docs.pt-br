---
title: Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ba5bbf34ecc12c2508c538e74909ee0a10aef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68461388"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Caixa de diálogo opções: \> compilação e execução de projetos e soluções

Nessa caixa de diálogo, você poderá especificar o número máximo de projetos de C++ ou C# que podem ser compilados ao mesmo tempo, determinados comportamentos de build padrão e algumas configurações de log de build. Para acessar essas opções, selecione **ferramentas**  >  **Opções** expandir **projetos e soluções**e, em seguida, selecione **Compilar e executar**.

**Número máximo de builds paralelos de projetos**

Especifica o número máximo de projetos de C++ e de C# que podem ser compilados ao mesmo tempo. Para otimizar o processo de build, o número máximo de compilações paralelas de projetos é automaticamente definido como o número de CPUs do seu computador. O máximo é 32.

**Somente compilar dependências e projetos de inicialização ao Executar**

Compila somente o projeto de inicialização e suas dependências quando você usa a tecla **F5**, o comando de menu **Depurar** > **Iniciar Depuração** ou os comandos aplicáveis no menu **Compilar**. Se ficar desmarcado, todos os projetos e dependências serão compilados.

**Ao Executar, quando os projetos estiverem desatualizados**

*Aplica-se somente a projetos de C++.*

Ao executar um projeto com **F5** ou com o comando **Depurar** > **Iniciar Depuração**, a configuração padrão **Avisar para compilar** exibe uma mensagem se a configuração do projeto estiver desatualizada. Selecione **Compilar sempre** para compilar o projeto sempre que ele for executado. Selecione **Nunca compilar** para suprimir todos os builds automáticos quando um projeto for executado.

**Ao Executar, quando ocorrerem erros de build ou implantação**

*Aplica-se somente a projetos de C++.*

Ao executar um projeto com **F5** ou com o comando **Depurar** > **Iniciar Depuração**, a configuração padrão **Solicitar inicialização** exibirá uma mensagem se o projeto precisar ser executado mesmo que o build tenha falhado. Selecione **Iniciar versão antiga** para iniciar automaticamente a última compilação boa, o que pode resultar em incompatibilidades entre o código em execução e o código-fonte. Selecione **Não iniciar** para suprimir a mensagem.

**Para novas soluções, use o projeto selecionado atualmente como o projeto de inicialização**

Quando essa opção é definida, novas soluções usam o projeto selecionado atualmente como o projeto de inicialização.

**Detalhamento da saída de build do projeto no MSBuild**

Determina a quantidade de informações do processo de build que é exibida na janela **Saída** janela.

**Detalhamento do arquivo de log de build do projeto no MSBuild**

*Aplica-se somente a projetos de C++.*

Determina a quantidade de informações gravada no arquivo de log de compilação, localizado em * \\ \<ProjectName> \debug \\ \<ProjectName> . log*.

## <a name="see-also"></a>Confira também

- [Compilando e criando](../../ide/compiling-and-building-in-visual-studio.md)
- [Caixa de diálogo Opções, Projetos e Soluções](projects-and-solutions-options-dialog-box.md)
- [Caixa de diálogo Opções, Projetos e Soluções, Projetos Web](options-dialog-box-projects-and-solutions-web-projects.md)
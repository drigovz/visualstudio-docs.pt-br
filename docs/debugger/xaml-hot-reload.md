---
title: Escrever e depurar XAML usando o recarregamento de hot de XAML
description: Recarregar hot de XAML ou XAML editar e continuar, permite que você faça alterações ao seu código XAML durante a execução de aplicativos
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a002c3876eecf0f31a8d104fa235b1208af90699
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929140"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Escrever e depurar o código XAML em execução com o recarregamento de hot XAML no Visual Studio

Visual Studio de XAML hot recarregar ajuda você a criar sua interface do usuário do aplicativo WPF ou UWP, permitindo que você faça alterações no código XAML, enquanto o aplicativo é executado. Esse recurso permite que você compilar e testar o código XAML com o benefício de contexto de dados do aplicativo em execução, o estado de autenticação e outra complexidade do mundo real que é difícil simular durante o tempo de design de forma incremental.

Recarregar hot de XAML é particularmente útil para esses cenários:

* Correção de problemas de interface do usuário encontrados no seu código XAML depois que o aplicativo foi iniciado no modo de depuração.

* Criar um novo componente de interface do usuário para um aplicativo que está em desenvolvimento, aproveitando as vantagens do contexto de tempo de execução do seu aplicativo.

|Tipos de aplicativos com suporte|Ferramentas e sistema operacional|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 ou versão posterior</br>Windows 7 e acima |
|Aplicativos universais do Windows (UWP)|Windows 10 e acima, com o [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Recarregar ativa do Visual Studio XAML está atualmente só tem suporte ao executar o aplicativo no Visual Studio com o depurador anexado (**F5** ou **iniciar depuração**). Você não pode habilitar essa experiência usando *anexar ao processo*.

## <a name="known-limitations"></a>Limitações conhecidas

A seguir é conhecidos limitações do XAML hot recarregar. Para contornar qualquer limitação que encontrar, simplesmente parar o depurador e, em seguida, concluir a operação.

|Limitação|WPF|UWP|Observações|
|-|-|-|-|
|Conectar eventos a controles, enquanto o aplicativo está em execução|Sem suporte|Sem suporte|Consulte o erro: *Verifique se o evento de falha*|
|Criando objetos de recursos em um dicionário de recursos, como aqueles na janela da página do seu aplicativo ou *App. XAML*|Sem suporte|Com suporte|Exemplo: adicionando um ```SolidColorBrush``` em um dicionário de recursos para uso como um ```StaticResource```.</br>Observação: Recursos estáticos, conversores de estilo e outros elementos escritos em um dicionário de recursos podem ser aplicadas/usados durante o uso de recarregamento XAML ativo. Não há suporte apenas a criação do recurso.</br> Alterar o dicionário de recursos ```Source``` propriedade.| 
|Adicionando novos controles, classes, windows ou outros arquivos ao seu projeto, enquanto o aplicativo está em execução|Sem suporte|Sem suporte|Nenhum|
|Gerenciamento de pacotes do NuGet (adição/remoção/atualização de pacotes)|Sem suporte|Sem suporte|Nenhum|
|Alterando a associação de dados que usa a extensão de marcação {X:Bind}|N/D|Com suporte no Visual Studio de 2019 e versões posteriores|Não tem suporte no Visual Studio de 2018 ou versões anteriores|

## <a name="error-messages"></a>Mensagens de erro

Você pode se deparar com os seguintes erros ao usar o recarregamento XAML ativo.

|Mensagem de erro|Descrição|
|-|-|-|
|Verifique se o evento de falha|O erro indica que você está tentando se conectar a um evento para um dos seus controles, que não tem suporte enquanto seu aplicativo está em execução.|
|O XAML Edit and Continue não encontrou nenhum elemento a ser atualizado.|Erro ocorre quando você estiver editando o XAML recarregar quente não é possível atualizar em seu aplicativo.</br> Esse erro, às vezes, pode ser corrigido por meio de seu aplicativo em execução para navegar até uma exibição em que o XAML é usado.</br> Às vezes, esse erro significa que a alteração específica que não pode ser aplicada até que você reinicie a sessão de depuração. |
|Não há suporte para essa alteração durante uma sessão de depuração.|Erro indica que a alteração que você está tentando executar não é suportada por recarregar hot de XAML. Parar a sessão de depuração, faça a alteração e, em seguida, reinicie a sessão de depuração.|
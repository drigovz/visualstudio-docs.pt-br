---
title: Noções sobre configurações de build
description: Este artigo descreve as várias configurações de build no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 911d8d3a65c414bc3c98494bda75c46b778e5b2b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584016"
---
# <a name="understanding-build-configurations"></a>Noções sobre configurações de build

Você pode armazenar diferentes configurações de propriedades da solução e do projeto para usar em diferentes tipos de builds durante o processo de desenvolvimento. Os projetos criados por Visual Studio para Mac usando um modelo normalmente incluirão configurações de depuração e versão que dão suporte à depuração de um aplicativo e à implantação de um aplicativo, respectivamente. 

Se você quiser criar configurações personalizadas, consulte [criando e editando configurações de compilação](./create-and-edit-configurations.md).

>[!NOTE]
>Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [entender as configurações de Build](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Configurações da solução

As configurações de solução são usadas para especificar configurações para todos os projetos em uma solução. Usando a guia **mapeamentos de configuração** no item **Compilar > configurações** , você pode atribuir uma configuração de destino para cada item na solução aberta. Isso é demonstrado na imagem a seguir:

![Opções de mapeamento de configuração](media/projects-and-solutions-image3.png)

Para saber mais sobre configurações, veja o vídeo do [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) de James Montemagno.

## <a name="project-build-configurations"></a>Configurações de build do projeto

Os projetos tendem a ter várias configurações. A configuração e a plataforma de destino de um projeto são usadas juntas para especificar as propriedades a serem usadas quando ele é compilado. Alternar entre configurações permite saídas diferentes no momento da compilação. Por exemplo, uma Configuração de depuração gerará a saída de símbolos de depuração, permitindo que o depurador resolva nomes de funções, parâmetros ou variáveis do rastreamento de pilha do aplicativo com falha. Embora essas informações adicionais sejam úteis durante o desenvolvimento, elas levarão a um tamanho de arquivo inflado e não é ideal para distribuição.

Cada plataforma tem configurações específicas para seu build. As páginas de configuração de compilação para projetos podem ser acessadas navegando até a seção **Build** na caixa de diálogo **Opções do projeto** . Abra essa caixa de diálogo clicando com o botão direito do mouse no projeto e selecionando **Opções** ou clicando duas vezes no projeto no Gerenciador de soluções.

## <a name="run-configuration"></a>Configuração de execução

Visual Studio para Mac permite definir uma configuração de _execução_. As configurações de execução são apresentadas em uma lista suspensa na barra de ferramentas, ao lado de seletor de configuração de build, conforme ilustrado abaixo:

![Lista suspensa Configuração de execução](media/projects-and-solutions-image8.png)

Uma configuração de execução é um conjunto de opções com um nome e várias configurações que são definidas em um projeto para finalidades diferentes. As configurações de execução são definidas no nível do projeto e um padrão será criado automaticamente para cada projeto executável, embora seja possível adicionar tantos quantos forem necessários. Certos tipos de projeto geram configurações de execução adicionais automaticamente. Por exemplo, projetos watchOS podem gerar _Configurações de visão rápida e de notificação._

As configurações podem ser compartilhadas com outros desenvolvedores (nesse caso, as configurações serão armazenadas no arquivo. csproj) ou mantidas localmente (nesse caso, elas serão armazenadas em um arquivo. User).

### <a name="android-run-configurations"></a>Configurações de execução do Android

As configurações de execução para projetos do Android permitem que a especificação de uma atividade, serviço ou receptor de difusão específico seja iniciada durante a execução ou a depuração do projeto. Você pode passar dados adicionais de tentativa e definir sinalizadores de intenção para testar seus componentes em condições de inicialização diferentes.

Atividades além de `MainLauncher` precisarão ter `Exported=true` adicionado ao atributo Atividade para a depuração em um dispositivo físico ou ter filtros de Intenção definidos.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Exemplos de dados que podem ser incluídos em configurações de execução

A lista a seguir fornece alguns exemplos de dados que podem ser incluídos em configurações de execução:

* Projeto .NET regular
  * Aplicativo de inicialização alternativo
  * Argumentos iniciais
  * Diretório de trabalho
  * Variáveis de ambiente
  * Opções de runtime Mono (deve ser usado somente quando em execução no Mono)
* Projeto do Android
  * Ponto de entrada (atividade, serviço, receptor)
  * Dados e os argumentos de intenção
* Projeto do iOS
  * Modo (Normal, Fetch em segundo plano)
* Projeto de extensão de iOS
  * Aplicativo de inicialização: padrão ou personalizada
* Projeto do WatchKit
  * Modo (Visão rápida, Notificação)
  * Conteúdo da notificação

## <a name="see-also"></a>Confira também

- [Noções sobre configurações de build (Visual Studio no Windows)](/visualstudio/ide/understanding-build-configurations)
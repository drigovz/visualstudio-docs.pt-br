---
title: Noções sobre configurações de build
description: Este artigo descreve as várias configurações de build no Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128407"
---
# <a name="understanding-build-configurations"></a>Noções sobre configurações de build

Você pode armazenar diferentes configurações de soluções e propriedades de projeto para usar em diferentes tipos de compilações durante o processo de desenvolvimento. Os projetos criados pelo Visual Studio para Mac usando um modelo normalmente incluem configurações de Debug e Release que suportam a depuração de um aplicativo e a implantação de um aplicativo, respectivamente. 

Se você quiser criar configurações personalizadas, consulte [Criar e editar configurações de compilação](/visualstudio/mac/create-and-edit-configurations).

>[!NOTE]
>Este tópico se aplica ao Visual Studio para Mac. Para o Visual Studio no Windows, consulte [Entenda configurações de compilação](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Configurações da solução

As configurações da solução são usadas para especificar configurações para todos os projetos em uma solução. Usando a guia **Mapeamentos de configuração** no item **Configurações de >,** você pode atribuir uma configuração de destino para cada item na solução aberta. Isso é demonstrado na seguinte imagem:

![Opções de mapeamento de configuração](media/projects-and-solutions-image3.png)

Para saber mais sobre configurações, veja o vídeo do [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) de James Montemagno.

## <a name="project-build-configurations"></a>Configurações de build do projeto

Os projetos tendem a ter múltiplas configurações. A configuração e a plataforma de um projeto são usados em conjunto para especificar as propriedades a serem usadas quando forem construídas. A comutação entre configurações permite saídas diferentes no tempo de construção. Por exemplo, uma Configuração de depuração gerará a saída de símbolos de depuração, permitindo que o depurador resolva nomes de funções, parâmetros ou variáveis do rastreamento de pilha do aplicativo com falha. Embora essas informações adicionais sejam úteis durante o desenvolvimento, elas levarão a um tamanho de arquivo inflado e não é ideal para distribuição.

Cada plataforma tem configurações específicas para seu build. As páginas de configuração de compilação para projetos podem ser acessadas navegando até a seção **Construir** na caixa de diálogo **Opções de** projeto. Abra esta caixa de diálogo clicando com o botão direito do mouse no projeto e selecionando **Opções** ou clicando duas vezes no projeto no explorador de soluções.

## <a name="run-configuration"></a>Configuração de execução

Visual Studio for Mac permite definir uma _configuração de execução_. As configurações de execução são apresentadas em uma lista suspensa na barra de ferramentas, ao lado de seletor de configuração de build, conforme ilustrado abaixo:

![Lista suspensa Configuração de execução](media/projects-and-solutions-image8.png)

Uma configuração de execução é um conjunto de opções com um nome e várias configurações que são definidas em um projeto para finalidades diferentes. As configurações de execução são definidas no nível do projeto, e um padrão será criado automaticamente para cada projeto executável, embora seja possível adicionar quantos necessários. Certos tipos de projeto geram configurações de execução adicionais automaticamente. Por exemplo, projetos watchOS podem gerar _Configurações de visão rápida e de notificação._

As configurações podem ser compartilhadas com outros desenvolvedores (nesse caso, as configurações serão armazenadas no arquivo .csproj) ou mantidas localmente (nesse caso, elas serão armazenadas em um arquivo .user).

### <a name="android-run-configurations"></a>Configurações de execução do Android

Executar configurações para projetos Android permite a especificação de uma determinada atividade, serviço ou receptor de transmissão para iniciar ao executar ou depurar o projeto. Você pode passar dados extras de intenção e definir sinalizadores de intenção para testar seus componentes em diferentes condições de lançamento.

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

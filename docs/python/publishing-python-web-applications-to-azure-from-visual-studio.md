---
title: Publicar um aplicativo do Python no Serviço de Aplicativo do Azure
description: Opções de publicação de um aplicativo do Python no Serviço de Aplicativo do Azure, incluindo implantação do Git, contêineres para Linux e implantação no IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 1f6d202bf51a31273eb4571bc6ff8ca497ec9a68
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159186"
---
# <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

No momento, o Python tem suporte no Serviço de Aplicativo do Azure para Linux. Você pode publicar aplicativos usando [Git deploy](#publish-to-app-service-on-linux-using-git-deploy) e [contêineres](#publish-to-app-service-on-linux-using-containers), conforme descrito neste artigo.

> [!Note]
> O suporte do Python no Serviço de Aplicativo do Azure para Windows foi oficialmente preterido. Como resultado, o comando **Publicar** do Visual Studio oficialmente tem suporte somente para um [destino IIS](#publish-to-iis). A depuração remota no Serviço de Aplicativo do Azure não tem mais suporte oficial.
>
> No entanto, os recursos para [Publicar no Serviço de Aplicativo no Windows](publish-to-app-service-windows.md) ainda funcionam por enquanto, pois as extensões do Python para o Serviço de Aplicativo no Windows permaneçam disponíveis, mas não terão manutenção nem atualizações.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publicar no Serviço de Aplicativo no Linux usando Git deploy

Git deploy conecta um Serviço de Aplicativo no Linux a uma ramificação específica de um repositório Git. A confirmação do código para essa ramificação implanta automaticamente o no Serviço de Aplicativo. O Serviço de Aplicativo instala automaticamente quaisquer dependências listadas em *requirements.txt*. Nesse caso, o Serviço de Aplicativo no Linux executa o código em uma imagem de contêiner pré-configurada que usa o servidor Web Gunicorn. No momento, esse serviço está em Versão prévia e não tem suporte para uso em produção.

Para saber mais, confira os seguintes artigos na documentação do Azure:

- [Início Rápido: Criar um aplicativo Web do Python no Serviço de Aplicativo](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) fornece um breve passo a passo sobre o processo de implantação do Git usando um aplicativo simples do Flask e a implantação por meio de um repositório Git local.
- [Como configurar o Python](/azure/app-service/containers/how-to-configure-python) descreve as características do Serviço de Aplicativo no contêiner do Linux e como personalizar o comando de inicialização do Gunicorn para seu aplicativo.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publicar no Serviço de Aplicativo no Linux usando contêineres

Em vez de depender do contêiner criado previamente com o Serviço de Aplicativo no Linux, você pode fornecer seu próprio contêiner. Essa opção permite que você escolha quais servidores Web usará e personalize o comportamento do contêiner.

Há duas opções para criar, gerenciar e enviar contêineres por push:

- Use o Visual Studio Code e a extensão do Docker, conforme descrito em [Implantar o Python usando contêineres do Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Mesmo que você não use o Visual Studio Code, o artigo fornece detalhes úteis para a criação de imagens de contêiner para aplicativos do Flask e do Django usando os servidores Web prontos para produção uwsgi e nginx. Depois, você pode implantar esse mesmo contêiner usando a CLI do Azure.

- Use a linha de comando e a CLI do Azure, conforme descrito em [Usar uma imagem personalizada do Docker](/azure/app-service/containers/tutorial-custom-docker-image) na documentação do Azure. No entanto, o guia é genérico e não é específico do Python.

## <a name="publish-to-iis"></a>Publicar no IIS

No Visual Studio, você pode publicar em uma máquina virtual do Windows ou em outro computador compatível com o IIS com o comando **Publicar**. Ao usar o IIS, crie ou modifique um arquivo *web.config* no aplicativo que informe ao IIS onde localizar o interpretador do Python. Para saber mais, confira [Configurar aplicativos Web do IIS](configure-web-apps-for-iis-windows.md).

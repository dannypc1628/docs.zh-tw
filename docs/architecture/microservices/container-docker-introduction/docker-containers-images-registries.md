---
title: Docker 容器、映像和登錄
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 容器、映像和登錄
ms.date: 08/31/2018
ms.openlocfilehash: 520f8d4d54f1fdd227ff9a1e88660b62e75f927f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674895"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="09720-103">Docker 容器、映像和登錄</span><span class="sxs-lookup"><span data-stu-id="09720-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="09720-104">使用 Docker 時，開發人員可以建立應用程式或服務，並將該應用程式或服務及其相依性封裝成一個容器映像。</span><span class="sxs-lookup"><span data-stu-id="09720-104">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="09720-105">映像是應用程式或服務及其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="09720-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="09720-106">為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。</span><span class="sxs-lookup"><span data-stu-id="09720-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="09720-107">這些容器一開始會在開發環境或電腦上進行測試。</span><span class="sxs-lookup"><span data-stu-id="09720-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="09720-108">開發人員應該將映像儲存在登錄中，該登錄可作為映像庫，而且在部署至生產協調器時需要用到。</span><span class="sxs-lookup"><span data-stu-id="09720-108">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="09720-109">Docker 會透過 [Docker Hub](https://hub.docker.com/) 維護公開登錄；其他廠商則會針對不同的映像集合提供登錄，包括 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="09720-109">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="09720-110">或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。</span><span class="sxs-lookup"><span data-stu-id="09720-110">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="09720-111">圖 2-4 顯示 Docker 中的映像和登錄與其他元件的關係。</span><span class="sxs-lookup"><span data-stu-id="09720-111">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="09720-112">它也顯示來自廠商的多個登錄供應項目。</span><span class="sxs-lookup"><span data-stu-id="09720-112">It also shows the multiple registry offerings from vendors.</span></span>

![Docker 中的基本分類：登錄就像是一個書架，映像會存放於此處，並供提取用以建置容器，以執行服務或 Web 應用程式。](./media/image5.PNG)

<span data-ttu-id="09720-117">**圖 2-4**：</span><span class="sxs-lookup"><span data-stu-id="09720-117">**Figure 2-4**.</span></span> <span data-ttu-id="09720-118">Docker 術語和概念分類</span><span class="sxs-lookup"><span data-stu-id="09720-118">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="09720-119">將映像放在登錄中可讓您儲存靜態和不可變的應用程式位元，包括其在架構層級的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="09720-119">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="09720-120">您可以接著在多個環境中建立這些映像的版本並加以部署，因此提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="09720-120">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="09720-121">建議在下列情況下使用私人映像登錄 (不論是裝載在內部部署或在雲端中)：</span><span class="sxs-lookup"><span data-stu-id="09720-121">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="09720-122">基於機密性，您的映像不得公開共用。</span><span class="sxs-lookup"><span data-stu-id="09720-122">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="09720-123">您想要在映像與所選擇的部署環境之間有最低的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="09720-123">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="09720-124">例如，如果您的生產環境是 Azure 雲端，您可以將映像儲存在 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) 中，使網路延遲盡可能縮短。</span><span class="sxs-lookup"><span data-stu-id="09720-124">For example, if your production environment is Azure cloud, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency will be minimal.</span></span> <span data-ttu-id="09720-125">同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。</span><span class="sxs-lookup"><span data-stu-id="09720-125">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="09720-126">[上一頁](docker-terminology.md)
>[下一頁](../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="09720-126">[Previous](docker-terminology.md)
[Next](../net-core-net-framework-containers/index.md)</span></span>
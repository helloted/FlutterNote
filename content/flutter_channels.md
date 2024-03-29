# Flutter版本区别
> 1

Flutter 具有以下通道，按稳定性的增加顺序排列：

### master

最新的版本。通常是功能性的，但有时会有一些bug。

### dev

最新的经过全面测试的版本。通常功能正常，但请参阅 Bad Builds 以获取已知“坏”开发版本的列表。我们不断尝试将 master 升级为 dev。这样做需要运行比我们在 master 开发期间运行的测试更多的测试，这就是为什么这实际上与 master 不同。

### beta

每个月，我们都会挑选上个月左右的“最佳”dev版本，并将其升级为测试版。这些已经通过我们的代码实验室进行了测试。

### stable

当我们相信我们有一个特别好的构建时，我们会将它提升到稳定的渠道。我们打算每个季度或多或少地这样做，但这可能会有所不同。我们建议您将此渠道用于所有生产应用程序版本。我们可能会针对高优先级错误将修补程序发送到稳定频道，尽管我们的目的是很少这样做。

[来源](https://github.com/flutter/flutter/wiki/Flutter-build-release-channels)




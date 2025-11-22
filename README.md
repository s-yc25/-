# 给定参考序列，基于多序列比对结果，对多序列进行截短

## STEP1：准备输入文件
1、参考序列文件：该文件应该是FASTA格式，包含目标参考序列。

2、多序列比对结果：该文件应为FASTA或其它多序列比对格式，包含待截短的序列集合。

3、（可选）比对的质量文件：如果需要使用比对质量信息来做进一步的筛选，可以提供对应的质量文件。

确保这些文件格式正确，并与工具要求的输入格式匹配。
## STEP2：执行多序列比对和对齐区域检测
在此步骤中，工具会根据输入的参考序列与多序列比对结果，分析对齐的区域，并确定截短的区间。

命令行示例：
```
shorten_sequences --reference reference_sequence.fasta --alignment alignment_results.fasta --output shortened_sequences.fasta
```
参数说明：

--reference：指定参考序列文件路径。

--alignment：指定多序列比对文件路径。

--output：指定输出文件路径，保存截短后的序列。

该步骤会生成一个包含截短序列的输出文件，其中所有序列都会根据参考序列的对齐区域进行裁剪。

## STEP3：验证截短结果
执行完截短操作后，建议对截短后的序列进行验证，确保序列截断正确。可以通过比对结果或者查看输出的序列文件进行检查。

例如，你可以通过以下命令对输出文件进行检查：
```
blastn -query shortened_sequences.fasta -subject reference_sequence.fasta
```
这样可以验证每个序列是否正确对齐于参考序列的预期区域。


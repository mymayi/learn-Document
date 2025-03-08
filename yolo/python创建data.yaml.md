```python
import os
import yaml

def generate_data_yaml(folder_path, output_path, dataset_path):
    # 获取文件夹中的所有文件名
    file_names = os.listdir(folder_path)
    
    # 去掉文件扩展名，假设文件名就是类别名称
    class_names = [os.path.splitext(file_name)[0] for file_name in file_names]
    
    # 创建 data.yaml 文件内容
    data_yaml = {
        'path': dataset_path,
        'train': 'JB./train',
        'val': '.JB/test',
        'nc': len(class_names),
        'names': class_names
    }
    
    # 写入 data.yaml 文件
    with open(output_path, 'w') as f:
        yaml.dump(data_yaml, f, sort_keys=False)
    
    print(f"生成的 data.yaml 文件已保存到 {output_path}")

if __name__ == '__main__':
    # 指定文件夹路径
    folder_path = 'JB-data/test'
    # 指定输出 data.yaml 文件的路径
    output_path = 'JB-data/data.yaml'
    # 指定数据集路径
    dataset_path = 'JB'
    
    generate_data_yaml(folder_path, output_path, dataset_path)

```


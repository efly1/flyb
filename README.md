### [👉👉👉♥♥点此进入♥观看入口👈👈👈](http://a.d44k.cc/17c.html)
<br></br><br></br><br></br>
        if 'outliers' in methods:
            # 处理异常值 - 使用IQR方法
            for col in data.select_dtypes(include=[np.number]).columns:
                Q1 = data[col].quantile(0.25)
                Q3 = data[col].quantile(0.75)
                IQR = Q3 - Q1
                lower_bound = Q1 - 1.5 * IQR
                upper_bound = Q3 + 1.5 * IQR
                data = data[(data[col] >= lower_bound) & (data[col] <= upper_bound)]
        
        self.processed_data = data
        return True
    
    def calculate_statistics(self):
        """计算基本统计量"""
        if self.processed_data is None:
            print("没有可分析的数据")
            return None
        
        numeric_data = self.processed_data.select_dtypes(include=[np.number])
        if numeric_data.empty:
            print("没有数值型数据可分析")
            return None
        
        stats = {
            'descriptive_stats': numeric_data.describe(),
            'correlation_matrix': numeric_data.corr(),
            'skewness': numeric_data.skew(),
            'kurtosis': numeric_data.kurtosis()
        }
        
        return stats
    

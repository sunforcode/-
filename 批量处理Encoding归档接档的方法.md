# 批量处理Encoding归档接档的方法 kVC原理


```
- (instancetype)initWithCoder:(NSCoder *)aDecoder {
    
    Persion *p = [Persion new];
    unsigned int count = 0;
    Ivar *ivar = class_copyIvarList([self class], &count);
    for (int i = 0; i < count; i++) {
        NSString *key = [NSString stringWithUTF8String:ivar_getName(ivar[i])];
        [p setValue:[aDecoder decodeObjectForKey:key] forKey:key];
    }
    return p;
}

- (void)encodeWithCoder:(NSCoder *)aCoder {
    unsigned int count = 0;
    Ivar *ivar = class_copyIvarList([self class], &count);
    for (int i = 0; i < count; i++) {
        NSString *key = [NSString stringWithUTF8String:ivar_getName(ivar[i])];
        [aCoder encodeObject:[self valueForKey:key] forKey:key];
    }
}
```
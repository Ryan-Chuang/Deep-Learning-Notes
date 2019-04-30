# k-Fold Cross-Validation
当训练集数据不够多时，预留大量的验证数据集是不明智的。而K-折叠交叉验证技术是指：将原始训练数据集分成K个非巧合的亚数据集（non-coincident sub-data set），然后模型训练和验证过程被重复K次。每次都采用一个亚数据集来验证模型，而采用其余K-1个亚数据集来训练模型。在K次训练和模型验证过程中，用于验证模型的亚数据集在K个亚数据集中逐个切换，最终，考虑K次训练和验证的平均值。
```python
def get_k_fold_data(k, i, X, y):
  assert k > 1
  fold_size = X.shape[0] // k
  X_train, y_train = None, None
  for j in range(k):
    idx = slice(j*fold_size, (j+1)*fold_size)     # slice start index and stop index
    X_part, y_part = X[idx, :], y[idx]
    if j == i:
      X_valid, y_valid = X_part, y_part
    elif X_train is None:
      X_train, y_train = X_part, y_part
    else:
      X_train = nd.concat(X_train, X_part, dim=0)   # concatrate two data arrays
      y_train = nd.concat(y_train, y_part, dim=0)
  return X_train, y_train, X_valid, y_valid
  
def k_fold(k, X_train, y_train, num_epochs, learning_rate, weight_decay, batch_size):
  train_l_sum, valid_l_sum = 0, 0
  for i in range(k):
    data = get_k_fold_data(k, i, X_train, y_train)
    net = get_net()
    train_ls, valid_ls = train(net, *data, num_epochs, learning_rate, weight_decay, batch_size)
    train_l_sum += train_ls[-1]
    valid_l_sum += valid_ls[-1]
    if i == 0:
      d2l.semilogy(range(1, num_epochs + 1), train_ls, 'epochs', 'rmse', range(1, num_epochs + 1), valid_ls, ['train', 'valid'])
    print('fold %d, train rmse: %f, valid rmse: %f '%(i, train_ls[-1], valid_ls[-1]))
  return train_l_sum/k, valid_l_sum/k
  ```

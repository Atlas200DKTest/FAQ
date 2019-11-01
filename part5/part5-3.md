## 5.3 ret=ai_model_manager->process是否支持多输入多输出场景
ret = ai_model_manager_->Process是支持多输入多输出的场景的，具体可以参考MindInferenceEngine1.cpp中的代码：
    // put buffer to FrameWork directly, InputSize has only one 
    hiai::AITensorDescription inputTensorDesc = hiai::AINeuralNetworkBuffer::GetDescription(); 
    for (int i = 0; i < predict_input_data_.size(); i++) { 
        std::map<uint8_t *, int> tmp = predict_input_data_[i]; 
        for (std::map<uint8_t *, int>::iterator it = tmp.begin();it != tmp.end(); ++it) { 
            shared_ptr<hiai::IAITensor> inputTensor = 
                hiai::AITensorFactory::GetInstance()->CreateTensor(inputTensorDesc, (void *)(it->first), it->second); 
            input_data_vec.push_back(inputTensor); // AIModelManager push input data 
        } 
     }

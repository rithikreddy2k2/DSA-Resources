# DSA-Resources
## Disjoint-Set-Union(DSU) (i.e.,Union-Find)
### https://leetcode.com/discuss/general-discussion/1072418/Disjoint-Set-Union-(DSU)Union-Find-A-Complete-Guide

model = {
    'type': 'RFLRecognizor',
    'transformation': {
        'type': 'TPS_SpatialTransformer',
        'F': 20,
        'I_size': (32, 100),
        'I_r_size': (32, 100),
        'I_channel_num': 1
    },
    'backbone': {
        'type': 'ResNetRFL',
        'input_channel': 1,
        'output_channel': 512
    },
    'neck_v2s': {
        'type': 'V2SAdaptor',
        'in_channels': 512
    },
    'neck_s2v': {
        'type': 'S2VAdaptor',
        'in_channels': 512
    },
    'counting_head': {
        'type': 'CNTHead',
        'embed_size': 512,
        'encode_length': 26,
        'loss_count': {
            'type': 'MSELoss',
            'reduction': 'mean'
        },
        'converter': {
            'type': 'RFLLabelConverter',
            'character': character
        }
    },
    'sequence_head': {
        'type': 'AttentionHead',
        'input_size': 512,
        'hidden_size': 256,
        'batch_max_length': 25,
        'converter': {
            'type': 'AttnLabelConverter',
            'character': character,
            'use_cha_eos': True
        },
        'loss_att': {
            'type': 'StandardCrossEntropyLoss',
            'ignore_index': 0,
            'reduction': 'mean',
            'loss_weight': 1.0
        }
    },
    'train_type': 'total',
    '_delete_': True
}


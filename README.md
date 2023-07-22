#!/usr/bin/env python
# coding: utf-8

# In[1]:


import json


# In[2]:


with open('reinv1.jsonl','r') as data_file:
    data = json.load(data_file)


# In[3]:


print(json.dumps(data,indent=4))


# In[4]:


with open("required_fields.txt",'r') as field_file:
    fields = field_file.read().splitlines()


# In[5]:


filtered_data = list()


# In[6]:


for dictionary in data['interimData']:
    temp = {}
    for key,value in dictionary.items():
        if key in fields:
            temp.update({key:value})            
    filtered_data.append(temp)


# In[7]:


data['interimData'] = filtered_data


# In[8]:


print(json.dumps(data,indent=3))


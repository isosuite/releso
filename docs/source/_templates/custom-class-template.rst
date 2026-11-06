{{ fullname | escape | underline}}

.. currentmodule:: {{ module }}

.. autoclass:: {{ objname }}
   :members:
   :inherited-members: releso.base_model.BaseModel
   :show-inheritance:

   {% block methods %}
   {% if methods and fullname not in [
    'releso.feature_extractor.FeatureExtractor',
    'releso.feature_extractor.CombinedExtractor'
   ] %}
   .. rubric:: {{ _('Methods') }}

   .. autosummary::
   {% for item in methods %}
   {% if item not in ['convert_to_pathlib_add_datetime', 'get_logger', 'set_logger_name_recursively'] %}
      ~{{ name }}.{{ item }}
   {% endif %}
   {%- endfor %}
   {% endif %}
   {% endblock %}

   {% block attributes %}
   {% if attributes %}
   .. rubric:: {{ _('Attributes') }}

   .. autosummary::
   {% for item in attributes %}
   {% if item not in ['save_location', 'logger_name'] %}
      ~{{ name }}.{{ item }}
   {% endif %}
   {%- endfor %}
   {% endif %}
   {% endblock %}
